---
title: "How do I uninstall Kubuntu"
date: 2005-10-25
forum: Desktop Environments
---

### Post by phil66 on 2005-10-25
I have Kubuntu Breezy 5.10

How do i unstall this distro and grub
Thanks

Ray

---

### Post by dbott67 on 2005-10-25
I'm assuming that you have a dual boot system with XP. If you want to get rid of grub, boot from your XP cd and get to the system recovery console. From the command prompt type:
```
fixmbr
``` For other versions of Windows (i.e. 98 or ME), boot from a Win98 boot floppy and type:
```
fdisk /mbr
``` This will overwrite grub and place Windows back in control of the Master Boot Record.

As for uninstalling Kubuntu, you can use the **Disk Management** tools in Windows (right-click **My Computer** & select **Manage**). Choose Disk Management and highlight the Linux partitition (might show up as unknown --- look for the one that is the same size as the partition you created) and then delete it. You can then partition and format it for use with Windows.


-Dave

---

### Post by haskan on 2005-10-25
[QUOTE=phil66]I have Kubuntu Breezy 5.10

How do i unstall this distro and grub
Thanks

Ray[/QUOTE]

well, what do you want to install after uninstalling kubuntu?

---

### Post by phil66 on 2005-10-25
Hi  dbott67

Thanks for the reply
The fdisk  /mbr is the items I was looking for.

Hi Haskan

I will either reinstall Ubuntu and add KDE to the distro or upgrade my Suse 9.3 to 10

Thanks to both of ya'll for the help.
Ray

---

