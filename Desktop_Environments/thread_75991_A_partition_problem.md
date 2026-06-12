---
title: "A partition problem"
date: 2005-10-14
forum: Desktop Environments
---

### Post by arj on 2005-10-14
I have a 120 GB IDE drive that Ubuntu install partitioned as follows:

IDE1 master (hda) - 120.0 GB WDC WD1200JB-00GVA0
 #1 Primary 255.0 MB ext3   /boot
 #5 Logical 119.8 MB  lvm
IDE1 slave...

LVM VG Ubuntu LV root - 118.2 GB Unknown
 #1 118.2 GB ext3
LVM VG Ubuntu LV swap_1 - 1.6 GB Unknown
 #1 1.6 GB swap

From the above I take it that I have a Volume Group named - **Ubuntu** which contains two Logical Volumes **root** and **swap_1**.
After the Ubuntu install I have upgraded to Kubuntu 5.10 RC.
The problem I now have is that the Disks Manager shows me the screenshot attached.
How can I use the 118.2 GB free space that it says is unavailable?
The second screenshot shows me the status I see within Konqueror when invoking System -> Storage Media from the panel. does this mean that the OS is using the entire drive space and has not lost any of the 118.2 GB free space?

---

### Post by HermanAB on 2005-10-14
Try the disk free command:
# df

and see if that gives sensible results.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by arj on 2005-10-14
Thanks. But I am newbie in Linux and you will have to interpret these results that were from that command: 
Filesystem 1K-blocks Used Available Use% Mounted on 
/dev/mapper/Ubuntu-root 113609368 3233972 104604340 3% / 
tmpfs 258260 0 258260 0% /dev/shm 
tmpfs 258260 12588 245672 5% /lib/modules/2.6.12-9-386/volatile 
/dev/hda1 233335 11951 208936 6% /boot

Do the above results mean they are ok?

---

### Post by brargh on 2005-11-26
[QUOTE=arj]Thanks. But I am newbie in Linux and you will have to interpret these results that were from that command: 
Filesystem 1K-blocks Used Available Use% Mounted on 
/dev/mapper/Ubuntu-root 113609368 3233972 104604340 3% / 
tmpfs 258260 0 258260 0% /dev/shm 
tmpfs 258260 12588 245672 5% /lib/modules/2.6.12-9-386/volatile 
/dev/hda1 233335 11951 208936 6% /boot

Do the above results mean they are ok?[/QUOTE]

Try ' df -h' for human readable output - it will give you info in megabytes instead of blocks :)

---

