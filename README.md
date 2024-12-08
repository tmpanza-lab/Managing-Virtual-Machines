# Managing Virtual Machines

## Objective

In this lab, we created and compared virtual machines to virtual machine scale sets. I learnt how to create, configure and resize a single virtual machine. I’ve learnt how to create a virtual machine scale set and configure autoscaling.

## Azure Virtual Machines Architecture diagram
![image](https://github.com/user-attachments/assets/6f1ca511-6c61-4c73-9da4-23fd174753e9)
 
### Job Skills

- Deploying zone-resilient Azure virtual machines by using the Azure portal.
- Managing compute and storage scaling for virtual machines.
- Creating and configuring Azure Virtual Machine Scale Sets.
- Scaling Azure Virtual Machine Scale Sets.
- Creating a virtual machine using Azure PowerShell (optional 1)
- Creating a virtual machine using the CLI (optional 2).


### Tools Used

- Azure portal - https://portal.azure.com
- Azure Cloud Shell
- Azure CLI (BASH)


## Steps


## Task 1: Deploy zone-resilient Azure virtual machines by using the Azure portal

In this task, I will deploy two Azure virtual machines into different availability zones by using the Azure portal. Availability zones offer the highest level of uptime SLA for virtual machines at 99.99%. To achieve this SLA, you must deploy at least two virtual machines across different availability zones.

1.	Sign in to the Azure portal - https://portal.azure.com.
2.	Search for and select Virtual machines, on the Virtual machines blade, click + Create, and then select in the drop-down Azure virtual machine. Notice your other choices.
![image](https://github.com/user-attachments/assets/10efbddd-e8ce-4cbe-97f9-dc04a017b767)
![image](https://github.com/user-attachments/assets/5db59176-20ac-4605-bdb2-3294133466a9)
![image](https://github.com/user-attachments/assets/6f51771c-aba4-4dbd-af9d-2100456a8fb3)
![image](https://github.com/user-attachments/assets/f1a06eea-c194-4fff-9cc3-6c3e261b958a)
![image](https://github.com/user-attachments/assets/1ca15ae7-17fc-4c21-bbf1-4795bf190ed1)
 


3.	On the Basics tab, in the Availability zone drop down menu, place a checkmark next to Zone 2. This should select both Zone 1 and Zone 2.
![image](https://github.com/user-attachments/assets/691a5b12-901b-47a2-86e5-b40668d2de6a)
![image](https://github.com/user-attachments/assets/e478a59e-4ad7-4f34-8d2d-1eb481e8663b)
  
4.	On the Basics tab, continue completing the configuration:
5.	Click Next : Disks > , specify the following settings (leave others with their default values):
![image](https://github.com/user-attachments/assets/e3e75ca1-babf-4168-95ab-a4634fa45010)
 
6.	Click Next : Networking > take the defaults but do not provide a load balancer.
![image](https://github.com/user-attachments/assets/371a08fc-2183-4e9c-89e2-19310aeffaee)
![image](https://github.com/user-attachments/assets/53c0de18-9871-4acf-b0c1-933dec7f17b7)
 
 
7.	Click Next : Management > and specify the following settings (leave others with their default values):
![image](https://github.com/user-attachments/assets/822c1bdb-3998-4c80-80e2-91a56ea5c427)
![image](https://github.com/user-attachments/assets/975f4849-77b7-43f7-ba35-16eba961b0c7)
 
 
8.	Click Next : Monitoring > and specify the following settings (leave others with their default values):
![image](https://github.com/user-attachments/assets/cd7dd8e0-48a1-4efb-afdc-9ef1cab08488)
![image](https://github.com/user-attachments/assets/1bc2e369-3e58-4906-81c0-280fb2180e22)
  

9.	Click Next : Advanced >, take the defaults, then click Review + Create.
![image](https://github.com/user-attachments/assets/2904e597-bd74-4b34-98d4-3ab914cf8cea)
 
10.	After the validation, click Create.
![image](https://github.com/user-attachments/assets/aafed7f7-d31f-4a41-b24d-e213d9be152b)
![image](https://github.com/user-attachments/assets/5dea7817-69b3-4078-a939-b676771efc49)

 
11.	Wait for the deployment to complete, then select Go to resource.


## Task 2: Manage compute and storage scaling for virtual machines

In this task, I will scale a virtual machine by adjusting its size to a different SKU. Azure provides flexibility in VM size selection so that you can adjust a VM for periods of time if it needs more (or less) compute and memory allocated. This concept is extended to disks, where you can modify the performance of the disk, or increase the allocated capacity.
![image](https://github.com/user-attachments/assets/ca1244f6-a34a-4aa5-85e5-9c88feb46e12)
 

1.	On the az104-vm1 virtual machine, in the Availability + scale blade, select Size.
2.	Set the virtual machine size to DS1_v2 and click Resize. When prompted, confirm the change.
![image](https://github.com/user-attachments/assets/25378aa3-9903-40da-bf5e-7d395452c05a)
![image](https://github.com/user-attachments/assets/c6e5c648-739e-41ca-a55d-5ca363967a18)
  
Resizing is also known as vertical scaling, up or down.
![image](https://github.com/user-attachments/assets/1016efe2-bc98-46f6-a224-29aa07032c29)
 
3.	In the Settings area, select Disks.
![image](https://github.com/user-attachments/assets/a5747e3f-aec7-459d-bf31-5d675dec9116)
 
4.	Under Data disks select + Create and attach a new disk. Configure the settings (leave other settings at their default values).
![image](https://github.com/user-attachments/assets/23afa5e9-8aa0-4ffc-ab98-accb107023ef)
 
5.	Click Apply.
6.	After the disk has been created, click Detach (if necessary, scroll to the right to view the detach icon), and then click Apply.
![image](https://github.com/user-attachments/assets/4e24887e-8899-4f64-bbab-49d27a5212ef)
 
## Note: Detaching removes the disk from the VM but keeps it in storage for later use.

![image](https://github.com/user-attachments/assets/f9f63514-dd22-41cc-87a7-5ec56adc539b)
 
7.	Search for and select Disks. From the list of disks, select the vm1-disk1 object.
![image](https://github.com/user-attachments/assets/7ce1e269-1fb6-4c92-a669-cc0f37bafc29)
![image](https://github.com/user-attachments/assets/ea5f0766-1bc8-4594-a45d-5df7fc45183b)
  
8.	In the Settings blade, select Size + performance.
9.	Set the storage type to Standard SSD, and then click Save.
![image](https://github.com/user-attachments/assets/31378bce-ed54-468a-8dc8-c94406cfc206)
 
10.	Navigate back to the az104-vm1 virtual machine and select Disks.
11.	In the Data disk section, select Attach existing disks.
12.	In the Disk name drop-down, select VM1-DISK1.
13.	Verify the disk is now Standard SSD.
![image](https://github.com/user-attachments/assets/ad8920e0-92ed-4873-bcc6-c3846ec9629a)
![image](https://github.com/user-attachments/assets/e5405ad8-0e19-43e5-8dcb-5f96f8ac8cbe)
  
## Note: I have now created a virtual machine, scaled the SKU and the data disk size. In the next task I use Virtual Machine Scale Sets to automate the scaling process.

14.	Select Apply to save your changes.


## Azure Virtual Machine Scale Sets Architecture Diagram
![image](https://github.com/user-attachments/assets/edff51a4-6a2b-45fa-a6fc-1ec736e88b26)
 

## Task 3: Create and configure Azure Virtual Machine Scale Sets

In this task, I will deploy an Azure virtual machine scale set across availability zones. VM Scale Sets reduce the administrative overhead of automation by enabling you to configure metrics or conditions that allow the scale set to horizontally scale, scale in or scale out.

1.	In the Azure portal, search for and select Virtual machine scale sets and, on the Virtual machine scale sets blade, click + Create.
![image](https://github.com/user-attachments/assets/3ff3d987-e873-44d3-8052-3822d7b8552a)
![image](https://github.com/user-attachments/assets/9530f0bf-30f7-4c79-8a01-55535a1ddd4f)
![image](https://github.com/user-attachments/assets/67811129-4ed8-40d0-b462-fac6ba8a0e6f)
 
 
2.	On the Basics tab of the Create a virtual machine scale set blade, specify the following settings (leave others with their default values) and click Next : Spot >:
![image](https://github.com/user-attachments/assets/5c93c914-1d67-4806-866c-58b3cf91c5bd)
 
3.	On the Spot tab, accept the defaults and select Next : Disks >.
4.	On the Disks tab, accept the default values and click Next : Networking >.
5.	On the Networking page, click the Create virtual network link below 
![image](https://github.com/user-attachments/assets/031e0132-5652-4470-9214-54632a0e1aee)
 
6.	the Virtual network textbox and create a new virtual network with the following settings (leave others with their default values). When finished, select OK.
7.	In the Networking tab, click the Edit network interface icon to the right of the network interface entry.
8.	For NIC network security group section, select Advanced and then click Create new under the Configure network security group drop-down list.
9.	On the Create network security group blade, specify the following settings (leave others with their default values):
 ![image](https://github.com/user-attachments/assets/528ee8ed-b063-412e-862a-e99aa84b4639)

10.	Click Add an inbound rule and add an inbound security rule with the following settings (leave others with their default values):
11.	Click Add and, back on the Create network security group blade, click OK.
12.	In the Edit network interface blade, in the Public IP address section, click Enabled and click OK.
![image](https://github.com/user-attachments/assets/cb6962a2-0e67-48fd-9a1e-06ab3c5130e1)
 
13.	In the Networking tab, under the Load balancing section, specify the following (leave others with their default values).
 ![image](https://github.com/user-attachments/assets/15b82975-5f9f-455a-b1cd-9bf8ab5a9924)

14.	On the Create a load balancer page, specify the load balancer name and take the defaults. Click Create when you are done then Next : Management >.
15.	On the Management tab, specify the following settings (leave others with their default values):
![image](https://github.com/user-attachments/assets/0c69041a-1dca-48e7-a0e6-3bc54c3671f7)
 
16.	Click Next : Health >.
17.	On the Health tab, review the default settings without making any changes and click Next : Advanced >.
18.	On the Advanced tab, click Review + create.
19.	On the Review + create tab, ensure that the validation passed and click Create.




## Task 4: Scale Azure Virtual Machine Scale Sets
In this task, you scale the virtual machine scale set using a custom scale rule.
1.	Select Go to resource or search for and select the vmss1 scale set.
2.	Choose Availability + Scale from the left side menu, then choose Scaling.
Scale out rule
1.	Select Custom autoscale. Then change the Scale mode to Scale based on metric. And then select Add a rule.
2.	Let’s create a rule that automatically increases the number of VM instances. This rule scales out when the average CPU load is greater than 70% over a 10-minute period. When the rule triggers, the number of VM instances is increased by 20%.
![image](https://github.com/user-attachments/assets/6b8a5206-79b7-4e21-9932-783fffc92c97)
 
3.	Be sure to Save your changes.
Scale in rule
1.	During evenings or weekends, demand may decrease so it is important to create a scale in rule.
2.	Let’s create a rule that decreases the number of VM instances in a scale set. The number of instances should decrease when the average CPU load drops below 30% over a 10-minute period. When the rule triggers, the number of VM instances is decreased by 20%.
3.	Select Add a rule, adjust the settings, then select Add.
![image](https://github.com/user-attachments/assets/a7ea97a1-1ed8-4e83-aefe-8791f6be0bfc)
 
4.	Be sure to Save your changes.

Set the instance limits
1.	When your autoscale rules are applied, instance limits make sure that you do not scale out beyond the maximum number of instances or scale in beyond the minimum number of instances.
2.	Instance limits are shown on the Scaling page after the rules.
 ![image](https://github.com/user-attachments/assets/76797ea5-18a9-4fe7-981c-8f8e6162bc41)

3.	Be sure to Save your changes
4.	On the vmss1 page, select Instances. This is where you would monitor the number of virtual machine instances.



## Task 5: Create a virtual machine using Azure PowerShell (option 1)

1.	Use the icon (top right) to launch a Cloud Shell session. Alternately, navigate directly to https://shell.azure.com.
![image](https://github.com/user-attachments/assets/f0d349ae-cfa8-4d61-84a2-5295479bb6f2)
 ![image](https://github.com/user-attachments/assets/e931728f-8da3-4533-acac-3954ada471c5)
 
2.	Be sure to select PowerShell. If necessary, configure the shell storage.
3.	Run the following command to create a virtual machine. When prompted, provide a username and password for the VM. While you wait check out the New-AzVM command reference for all the parameters associated with creating a virtual machine.
![image](https://github.com/user-attachments/assets/a0a5c935-a420-4418-81e3-46275c4c7a1c)
![image](https://github.com/user-attachments/assets/bb27db94-4fb7-45fd-ad30-6f1dfe1b91bc)
  
4.	Once the command completes, use Get-AzVM to list the virtual machines in your resource group.
 ![image](https://github.com/user-attachments/assets/426939fb-3747-41ca-bda7-5c04bf886e87)

5.	Verify your new virtual machine is listed and the Status is Running.
6.	Use Stop-AzVM to deallocate your virtual machine. Type Yes to confirm.
![image](https://github.com/user-attachments/assets/60ca0550-72c3-4f35-8447-034aa421aee6)
 
7.	Use Get-AzVM with the -Status parameter to verify the machine is deallocated.
![image](https://github.com/user-attachments/assets/2bd5e1ff-8f3c-4452-8ff2-069e7cc2218b)
 
## Task 6: Create a virtual machine using the CLI (option 2)
![image](https://github.com/user-attachments/assets/debc9d0d-ae5a-4e68-b303-dfe7a395f904)

 
1.	Use the icon (top right) to launch a Cloud Shell session. Alternately, navigate directly to https://shell.azure.com.
![image](https://github.com/user-attachments/assets/11b25c99-d82c-4763-84de-969c9d301bd0)
![image](https://github.com/user-attachments/assets/2fcea71a-fb2f-4fb4-a338-40d1adfcedc5)
 
 
2.	Be sure to select Bash. If necessary, configure the shell storage.
3.	Run the following command to create a virtual machine. When prompted, provide a username and password for the VM. While you wait check out the az vm create command reference for all the parameters associated with creating a virtual machine.
4.	Once the command completes, use az vm show to verify your machine was created.
 ![image](https://github.com/user-attachments/assets/c4c06341-f4c4-4a9e-8c27-919cf75e4afb)

5.	Verify the powerState is VM Running.
6.	Use az vm deallocate to deallocate your virtual machine. Type Yes to confirm.
 ![image](https://github.com/user-attachments/assets/1186da3b-8723-41cf-90e1-69e2342c46cb)

7.	Use az vm show to ensure the powerState is VM deallocated.
 ![image](https://github.com/user-attachments/assets/c21f82a7-ee4c-4cd1-9cf1-72dd1119166e)


## Cleanup your resources
If you are working with your own subscription take a minute to delete the lab resources. This will ensure resources are freed up and cost is minimized. The easiest way to delete the lab resources is to delete the lab resource group.
![image](https://github.com/user-attachments/assets/8b94b2d6-fa87-4b7b-bcd5-bfb487cad27d)
 
-	In the Azure portal, select the resource group, select Delete the resource group, Enter resource group name, and then click Delete.
-	Using Azure PowerShell, Remove-AzResourceGroup -Name resourceGroupName.
![image](https://github.com/user-attachments/assets/7970cb11-e184-4c05-b887-0ffdcc99b00a)
 
-	Using the CLI, az group delete --name resourceGroupName.
 ![image](https://github.com/user-attachments/assets/027996ef-b626-4cc4-8621-59db49776fed)
![image](https://github.com/user-attachments/assets/bf5ef4f1-67ce-4118-81ba-3730dc704971)

 
## Key takeaways

Here are the main takeaways for this lab.

- Azure virtual machines are on-demand, scalable computing resources.
- Azure virtual machines provide both vertical and horizontal scaling options.
- Configuring Azure virtual machines includes choosing an operating system, size, storage and networking settings.
- Azure Virtual Machine Scale Sets let you create and manage a group of load balanced VMs.
- The virtual machines in a Virtual Machine Scale Set are created from the same image and configuration.
- In a Virtual Machine Scale Set the number of VM instances can automatically increase or decrease in response to demand or a defined schedule.

