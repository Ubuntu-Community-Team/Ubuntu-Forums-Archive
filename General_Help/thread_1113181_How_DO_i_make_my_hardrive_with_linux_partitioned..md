---
title: "How DO i make my hardrive with linux partitioned."
date: 2009-04-01
forum: General Help
---

### Post by tanveerahmed2k8 on 2009-04-01
well i have to 2 harddrives. 1 is 80gb the other is 200gb and i hav xp on the 80gb hardrive and ubuntu on the 200gb harddrive, how do i partition the ubuntu/200gb harddrive, to 50gb an haaaaave 150gb as a ntfs.
so i can use that for xp sp3. or windows 7.

---

### Post by markharding557 on 2009-04-01
you can use gparted you will have to use it from a live cd because it will need your drive unmounted in order to work.

---

### Post by ajitem on 2009-04-01
First of all use GParted or any other partition utility to shrink the 200GB drive to 50GB. This way you will get a 50GB Ubuntu Partition and leave you with 150gigs of free space. You can install the OS of your choice on the other 150gb partition. Just remember to take a backup of the GRUB loader so you can restore it at a later stage and use both the OSeS hassel free !

To Backup GRUB,
Firstly, boot into Ubuntu and go to Applications --> Accessories --> Terminal. Then, type in sudo gedit /boot/grub/menu.lst.

This text file contains all the information GRUB uses to configure various boot options. Scroll down and the entries between "## ## End Default Options ##" and "### END DEBIAN AUTOMATIC KERNELS LIST" are the Linux boot options.

Make a backup of the file by going to File, Save As and selecting a different location. Or take a full copy of the contents and place it into a new text file. If you can, create the backup on a removable disk or networked location.

Once XP has been installed, it will boot happily into XP but there's no sign of Ubuntu. To reinstate GRUB as the system bootloader it needs to be reinstalled into the MBR.

Boot the system from the Ubuntu Live CD and select "Try Ubuntu without any change to your computer".

Next, open the Terminal and enter the GRUB configuration mode by typing "sudo grub: without the quotes and enter the following commands sequentially :
- root (hd0,0)
- setup (hd0)
- quit
- exit 

Reboot the system. You'll get the GRUB bootloader but XP won't be an option - we need to add this to the boot options.

Boot into Ubuntu and open up another Terminal session. Then, type in sudo gedit /boot/grub/menu.lst

Scroll down to the bottom of the file and type in the following text strings:

title Windows XP
root (hd0,1)
makeactive
chainloader +1

Save the file and reboot. When the GRUB loader launches hit ESC for the boot menu. Windows XP is the last option - select it and XP will load.

If you want to make the GRUB menu always available, boot back into Ubuntu and edit the MENU.LST file. Find the hiddenmenu text string and change it to #hiddenmenu.

To increase the menu timeout, change the default timeout 3 to something more appropriate.

NOTE :- Though its possible to install XP over Ubuntu, the fact that XP insists that it should be install on the first partition makes things complicated. I'd rather take a backup, install XP and then Ubuntu over it. It would be easier and somewhat faster with a little less risk to lose data.

---

### Post by markharding557 on 2009-04-01
i think it would be simpler or the op to reinstall windows and then use the ubuntu installer to resize and install ubuntu?

---

### Post by ajitem on 2009-04-01
Yes. Much Easier. To make things more easier, while you install XP make partitions in such a way that you won;t need to shrink/resize later on.

---

