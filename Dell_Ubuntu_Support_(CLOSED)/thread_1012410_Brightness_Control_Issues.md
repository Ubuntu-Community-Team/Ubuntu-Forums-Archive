---
title: "Brightness Control Issues"
date: 2008-12-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JRCavileer on 2008-12-15
Specifically: If I adjust the brightness the keyboard stops working aside the Fn and up and down arrows (only allowing me to adjust the brightness). Also the right click on the mouse stops working and i cant drag or select anything on the desktop.

I have a m1330 with 8.10.
If any more information is required let me know, and thank you in advanced!

---

### Post by superm1 on 2008-12-16
Turn on the proposed repository.  There are some bugs in the kernel that get fixed from it.

---

### Post by homunculus on 2008-12-19
> **superm1 said:**
> Turn on the proposed repository.  There are some bugs in the kernel that get fixed from it.

Could someone translate this into n00b for me?  I'm having almost the exact same issue on my Inspiron 630m with 8.10 -- and I just got started with Ubuntu a few days ago.

Thanks in advance!

---

### Post by Spoonite on 2008-12-24
> **homunculus said:**
> Could someone translate this into n00b for me?  I'm having almost the exact same issue on my Inspiron 630m with 8.10 -- and I just got started with Ubuntu a few days ago.

Thanks in advance!

I had the same problem on an Inspiron 630m but with Mint 6 (Felicia). What superm1 means is this:

1- Open Synaptic Package Manager.
2- Click on Settings and then click Repositories in the drop down menu.
3- Scroll down until you see a deb URI with 'intrepid-proposed' in the Distribution column and enable it (make sure its the deb type and not deb-src). Then click ok.
4- Click 'Reload' in Synaptic and once thats completed click 'Mark All Upgrades'. You should see that a new kernel has been marked for installation. In my case it was 2.6.27-11.
5- If you don't want to install all the updates you can unclick the ones which are unrelated to the kernel. Once you're ready click Apply.

For me menu.lst was not updated to use the new kernel when booting so i had to update it myself. menu.lst is the file the Grub boot loader refers to when booting an OS. You need to be extremely careful when editing this file as if you enter anything incorrectly you will need a live CD to get back into your system to fix it again. But anyways, here is how you do it:

1- Open the terminal and type in 'sudo gedit /boot/grub/menu.lst'. 
2- This will prompt you for your password so enter it and then gedit should open the menu.lst file. It may be a good idea to save a backup of menu.lst on your desktop in case you accidentally make a mistake when editing this file.
3- Scroll down (towards the bottom) till you see something like this...

title		Ubuntu 8.10
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

All you need to do is update the kernel number. You can double check the latest kernel you have by opening /boot/grub and then looking for the highest numbered initrd.img-2.6.27-XX-generic file. In my case it was 2.6.27-11 so after the changes it looked like this... (without the boldness :) )

title		Ubuntu 8.10
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-**11**-generic root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-**11**-generic
quiet

4- Save your changes and reboot your computer.

Your brightness/keyboard problem should now be fixed!! 

**NOTE:**
If you computer doesn't boot then I would get a live CD and mount the partition that Ubuntu or whatever is installed on and then replace the altered menu.lst file with the backup one you hopefully save to your desktop. If you didn't save a backup then I would find someone who knows what they're doing to restore things back to normal for you. 
As a last resort you could reinstall grub on your system. But I'm not gonna talk about that. There are heaps of tutorials on this forum which discuss that.

Cheers, hope that helps! :KS

---

