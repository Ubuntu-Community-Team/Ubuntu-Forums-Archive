---
title: "GRUB removal - MBR restoration. Very specific situation."
date: 2008-12-31
forum: General Help
---

### Post by Rfgordils on 2008-12-31
I have installed Ubuntu as a dual-boot along with Windows XP on a family member's computer. That family member does not want Linux or the GRUB menu to remain on that computer. Removing Ubuntu will be easy, but I can't seem to find a way to remove GRUB.

I've Googled endlessly for a solution, but none of these solutions will work for me.

Solution 1) Use the Windows XP boot disk to restore the MBR using the fdisk /mbr command.  

This doesn't work for me because I don't have any sort of Windows boot Disk handy. I have tried downloading free boot disks from BootDisk.com but I don't have a floppy drive to run any of them. I also do not know how to burn/convert one of these boot disks into something that can be put onto a CD.

Solution 2) Use an Ubuntu LiveCD to restore MBR. 

This doesn't work because this solution requires me to download packages from online. Ubuntu doesn't seem to like my wireless driver, so I can't go online. I could try to use ndis wrapper to fix the driver, but I have to download ndis wrapper to Ubuntu first, which I cannot, because even a direct ethernet connection doesn't work.

I have to have GRUB removed and MBR restored within the next couple of days before I leave. I'm still very much a newbie to Linux, so any help would be greatly appreciated, thank you!

---

### Post by adult swim on 2008-12-31
you can fix windows mbr without downloading anything from the ubuntu live cd.  open a terminal applications>accessories>terminal and run ```
sudo lilo -M /dev/sda mbr
``` assuming that windows is on the drive sda

---

### Post by dcstar on 2008-12-31
> **Rfgordils said:**
> 
........
I have to have GRUB removed and MBR restored within the next couple of days before I leave. I'm still very much a newbie to Linux, so any help would be greatly appreciated, thank you!

Last time I did a Google search there were many freeware utilities to restore the Windows boot sector, try one of them.

---

### Post by melojo on 2008-12-31
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by 2hot6ft2 on 2008-12-31
> **Rfgordils said:**
> 
Solution 1) Use the Windows XP boot disk to restore the MBR using the fdisk /mbr command.  

This doesn't work for me because I don't have any sort of Windows boot Disk handy. I have tried downloading free boot disks from BootDisk.com but I don't have a floppy drive to run any of them. I also do not know how to burn/convert one of these boot disks into something that can be put onto a CD.

Solution 2) Use an Ubuntu LiveCD to restore MBR. 

This doesn't work because this solution requires me to download packages from online. Ubuntu doesn't seem to like my wireless driver, so I can't go online. I could try to use ndis wrapper to fix the driver, but I have to download ndis wrapper to Ubuntu first, which I cannot, because even a direct ethernet connection doesn't work.
So 1 you have no tools with which to do it and 2 you can't get any tools to do it.

But in 1 you said you downloaded. So if you can in fact download then this may be your best option. If you can go here [http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/) and download the vista recovery disc (cd iso, assuming you know how to burn that) it may let you fix the MBR even though you have xp.

Another one would be getting a livecd from here which could also fix the MBR [http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

I don't know if you could do it without a disc by selecting Recovery when starting windows or not, I do know Recovery is an option unless it's been changed.

---

### Post by Rfgordils on 2009-01-01
I downloaded and burned the Vista boot CD in the link, but when I tried 'Startup Repair' with it, it told me "Windows cannot repair this computer automatically". When I go to diagnostic and repair details, it shows that the Root Cause is "Boot manager is missing or corrupt." 
I also tried going into the Command Prompt and using the 'FIXMBR' command and the 'fdisk /mbr' command, but it didn't recognize either command.

I've also tried some freeware, such as MBRFix, but for some reason it wouldn't work on this computer. I don't know if I'm doing something wrong, or if there's some other reason. When I use MBRFix, it opens a dos window for about half a second, then immediately closes it.

The sudo lilo -M /dev/sda mbr command didn't work for me either. The terminal replied with something along the lines of not recognizing the command or not recognizing the directory. (Sorry, I'm respond through Windows and didn't get around to documenting the exact response).

I'm about to try supergrubdisk.org and see how it works for me.

Thanks everyone, for all of your feedback. Some of these solutions might not be working because I'm doing something wrong. I hope this last try works.

---

### Post by adult swim on 2009-01-01
with vista recovery cd, you need to enter in ```
bootrec /fixmbr

bootrec /fixboot
``` from the command prompt

---

