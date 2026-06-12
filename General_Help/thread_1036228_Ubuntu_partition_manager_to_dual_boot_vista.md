---
title: "Ubuntu partition manager to dual boot vista"
date: 2009-01-10
forum: General Help
---

### Post by ~farah_r~ on 2009-01-10
Solved: BUT, now i have problems with partitions when i install ubuntu on vista dual booting both!!!

Hi,

I installed ubuntu on my vista machine but it wiped out vista. I have working linux now, but want to dual boot it with vista by installing vista. I followed the steps given below in a guide online: ([http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=4))

But, when it comes to the last step (step 8), it does not list this unallocated space partition. It only lists the partition on which linux is installed and not the unallocated space partition.

Do I have to do something to this unallocated space partition to make it ntfs system or something? Cos the guide did not mention this part...I did not want to risk something again and end up losing this hard drive space...

EDIT: I made it a ntfs partition and i made it active. But, when I try to install vista, it says:
Windows is unable to find a system volume that meets its criteria for installation.

Can any1 help me out...this is so frustrating!

Thanks,
Farah.

1. Download the Gnome Partition Editor from here or use the Ubuntu Live CD to partition your drive. We will use the Gnome Partition Editor

2. Boot from the live CD and press ENTER twice to select your language and keyboard layout

3. Right click on /dev/sda1 (depending on how you have your drive partitioned, this may be different) and click Resize/Move

4. Move the slider to select how much space you need for Vista and Resize/Move

5. When you&#8217;re finished, quit GNOME Partition Editor, restart your computer and boot from the Vista DVD

6. Follow the instructions form the Vista installer until you get to the Where do you want to install Windows? page.

7. When you&#8217;re there, select Unpartitioned Space and click Next

8. Press SHIFT + F10 to launch a command window, then type in DISKPART and press Enter.

Select the active disk by typing in "SELECT DISK 0".

List the partitions by typing in "LIST PARTITION". The newly-created NTFS partition is PARTITION 3.

Select this partition by typing in "SELECT PARTITION 3", and then type in "ACTIVE".

---

