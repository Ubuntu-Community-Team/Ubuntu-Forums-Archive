---
title: "create usb startup disk not working"
date: 2009-02-02
forum: General Help
---

### Post by geyids on 2009-02-02
Hi. im I supposed to have a special USB disk for the create a USB start-up disk to work? I tried and it installs nothing in my USB drive. doesn't copy even a single files.

Please help

---

### Post by zwygart on 2009-02-02
Along me it should be possible to make bootable most storage Devices (including USB drives). I work a lot with Flash USB booted OS's. 
The drive must be enough big (1G min). 

So some questions : how big is your disk?
When you plug in the drive what is the output of fdisk -l?

I never used the automatic installer of ubuntu. Now I know how, I prefer install every OS manually on my drive.

---

### Post by geyids on 2009-02-02
Its a 2GB flash disk. I have also tried from a 40GB external usb drive but none is working and no errors. fdisk -l has alot of output. do I post it all here?
How do you install that manually? maybe its the best with better options.

Regards

---

### Post by zwygart on 2009-02-02
To post a output select it with the mouse, press CTRL+SHIFT+C, in the post press CTRL+V and the work is done. In my case no need to post all the output, the section of the USB drive is enough. 

They are methods to compile and install grub but they are not easy. The easiest way is to copy the grub files from a installed Ubuntu. Copy the content of /boot/grub on your drive in boot/grub. Then from a terminal type grub or during the boot type c. This will bring you to a GRUB shell. Type these commands 
```
find /boot/grub/stage1
root (hdX,Y)
setup (hdX)
```

Replace X and Y with the output of find wich correspond to your drive. Be carefull, an error may make your system unbootable without your drive plugged.

Now your drive is bootable but no OS on it. Put the os you want (copy the content of a ISO ot the root), and edit boot/grub/menu.lst in accordance to what you putted. 

My LiveCD Ubuntu 8.10 is started by
```
title live
root (hd0,5)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper
initrd /casper/initrd.gz quiet splash --

title live-install
root (hd0,5)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity
initrd /casper/initrd.gz quiet splash --

title check
root (hd0,5)
kernel /casper/vmlinuz boot=casper integrity-check 
initrd /casper/initrd.gz quiet splash --
```
(hd0,5) is the grub partition where I putted Ubuntu, your will be different.



For a more customizable install of grub type help install at the grub shell.

---

### Post by geyids on 2009-02-05
I tried the above but I noticed, find /boot/grub/stage1 worked only when I 'sudo grub' as a normal user it didnt work. I installed as root but after reboot still the USB drive can't boot. I copied the OS too to the drive.

---

### Post by zwygart on 2009-02-05
What does happen on start up? An error, nothing?
Did you choosen to boot on USB on start up? Press A F? key, enter, tab or something. It should be written on the screen on start up. This will bring you to a menu from where you can choose the boot device.
Is your computer able to boot USB, if older than 4 years than porbably not. 

Please post the output of the boot_info_script (The key must be plugged). From [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
This will help me to see how your system is setted.

---

