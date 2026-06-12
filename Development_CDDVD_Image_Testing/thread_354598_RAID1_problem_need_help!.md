---
title: "RAID1 problem need help!"
date: 2007-02-06
forum: Development CD/DVD Image Testing
---

### Post by Bunro on 2007-02-06
These are the steps I made:
 During startup procedure push DEL to enter the BIOS.
 Under Advanced BIOS Features set ATA RAID or SCSI Card Boot to RAID
 Under Integrated Peripherals > Onboard PCI Device > High Point IDE RAID set Enabled
 Save setting on exit.
 

 During startup fase:
 CTRL-H to enter the High Point BIOS settings
 [LIST=1]
[*]Create Array > Select RAID1 > 	Create only
[*]Array name > enter > enter 	Leaving it standard RAID_1_0
[*]Select Disk Drives > selecting 	both HD (both are WD HD 250 GB)
[*]Start Creation Process 
WARNING: 	All data on the selected disks will be deleted. Continue > Yes
[/LIST] Check press F1 View Channel Status
 Array Name:	RAID_1_0
 Array Mode:	RAID 1 (Mirroring)
 Block Size:	N/A
 Size (GB):	250.05
 Esc to exit the BIOS.
 

 After this step I followed the steps in the following link:
 [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)
 

 After I partitioned the two HD in:
 /	20.0 GB  Boot
 /swap	2.0 GB
 /home	the rest
 

 I getting the following ERROR  
 [!! Partition disks]
 Could not stat device /dev/md/2 – No such file or directory.
 ERROR!!!
 Retry
 Cancel
 <Go Back>
 

 Hopefully there is some one that can help me out! I would like to setup a RAID1 system using Ubuntu 7.04 a3 or Ubuntu 6.10.
 

 Please let me now what I am doing wrong here and if possible step by step instructions?
 

 Regards, Robert

---

### Post by pochu on 2007-02-07
I think this is not the right forum to post this. This is form ISO testing. This is not a problem in the Iso images, but in the harware configuration.

Henrik, or any admin, I think this should go to the hardware&laptops forum.

If I'm right, please, move it.

Bunro, about the question, I have no idea. Sorry

---

