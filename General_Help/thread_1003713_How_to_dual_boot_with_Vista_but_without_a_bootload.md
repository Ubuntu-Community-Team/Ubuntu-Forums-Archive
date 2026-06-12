---
title: "How to dual boot with Vista but without a bootloader?"
date: 2008-12-06
forum: General Help
---

### Post by ti89hp48gx on 2008-12-06
I have Vista and a 640gb HD, want to toss Ubuntu on a 20GB partition im going to make. I rarely use it so I dont want to have to deal with a lunux bootloader screen like grub coming up and delaying my boot time. Is there some file you can edit or something?

---

### Post by lovelyvik293 on 2008-12-06
You can minimize the boot time by editing the /boot/grub/menu.lst.And even You can just make the vista default boot without any delay or minimum delay with this file.

---

### Post by TeXtonyx on 2008-12-06
> **ti89hp48gx said:**
> I have Vista and a 640gb HD, want to toss Ubuntu on a 20GB partition im going to make. I rarely use it so I dont want to have to deal with a lunux bootloader screen like grub coming up and delaying my boot time. Is there some file you can edit or something?

You can also install grub to Ubuntu's /boot partition during 
Step 7, Advanced. Then download free Easybcd and add Ubuntu
to the Windows boot menu. 

Before, shrink the Vista partition 20GB using the Vista resizer. 
During the live cd install, choose 'use largest continuous space'
and Ubuntu will use that 20GB of unallocated space you created.

This method works really well, no danger of overwriting Vista
or damaging the boot sector. The grub menu will show up after
you select Ubuntu from Vista. I make it so that I could boot
Vista from Ubuntu also. There is a handy too called Super Grub
Disk that will boot Ubuntu from that /boot partition. That is
a good idea in case Vista has a problem, you can send email and
use the internet to find fixes. Finally, there is a program named
LinuxReader (free) which lets you view the Ubuntu files and save
them over to the Vista partition which can be useful.

---

### Post by cdtech on 2008-12-06
Install GRUB on the Ubuntu partition (outside of the MBR)

On Ubuntu, launch a Terminal with root privileges

Install GRUB on the Ubuntu partition by running:
```
grub-install /dev/sda1 (or whatever your Ubuntu is installed on)
```
Get a copy of the Ubuntu boot sector:
```
dd if=/dev/**sda1** of=/tmp/ubuntu.bin bs=512 count=1 (use your own device here)
```
Copy the newly created ubuntu.bin on a FAT formatted USB key or any storage device accessible from Windows Vista.

Create an entry for GRUB in Windows Vista boot configuration data store using bcdedit.

On Windows Vista, launch a command prompt with administrative privileges (by right clicking on cmd and choosing Run as Administrator).

Copy the Ubuntu boot sector (ubuntu.bin) on the root of the Windows boot (active) partition, namely the one containing bootmgr. If you don&#8217;t know for sure you can use diskpart or diskmgmt.msc to find out which one it is.

Create an entry for GRUB :
```
bcdedit /create /d &#8220;GRUB&#8221; /application BOOTSECTOR
```
**Note:** bcdedit will return an ID for this entry we'll call {UbuntuID} below. You will need to replace {UbuntuID} by the returned identifier in this step. An example of {UbuntuID} is {81ed7925-47ee-11db-bd26-cbb4e160eb27}

Specify which device hosts a copy of the Ubuntu boot sector
```
bcdedit /set {UbuntuID} device boot
```
Specify the path to a copy of the Ubuntu boot sector
```
bcdedit /set {UbuntuID}  PATH \ubuntu.bin
```
Add the Ubuntu entry to the displayed menu at boot time
```
bcdedit /displayorder {UbuntuID} /addlast
```
Let the menu be displayed 10 seconds to allow for OS selection
```
bcdedit /timeout 10
```

---

