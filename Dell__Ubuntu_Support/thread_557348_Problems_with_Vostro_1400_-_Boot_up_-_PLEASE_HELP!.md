---
title: "Problems with Vostro 1400 - Boot up - PLEASE HELP!!"
date: 2007-09-22
forum: Dell  Ubuntu Support
---

### Post by bighead0618 on 2007-09-22
I'm having trouble booting up Ubuntu.

I followed the "Dell Vostro Ubuntu How To" thread for installation and video driver setup.

When I reboot, i get an error and it goes to the command screen. 
"/bin/sh: can't access tty; job control turned off"
I then enter the...
modprobe piix
exit ... as described by the thread.

The below problem was corrected after reinstalling the NVIDIA drivers several times...  HOWEVER, how do I  fix the above so that it starts up normally??

Then I get an error that it failed to start xserver. I then have to reinstall the Nvidia driver and restart xserver for me to get the GUI interface.

My xorg.conf looks like:
Section "Device"
   Identifier   "Device0"
   Driver        "nvidia"
   VendorName  "NVIDIA Corporation"
EndSection

---

### Post by saru411 on 2007-09-22
bibou91 <---look for his first post in

[http://ubuntuforums.org/showthread.php?t=521753](http://ubuntuforums.org/showthread.php?t=521753)

he give the commands there. if you are lazy here you go

> sudo -i
echo piix >> /etc/initramfs-tools/modules    
sudo update-initramfs -u

Then you have to edit /boot/grub/menu.lst and make look your entries like that (You should remove break=top) 

this is done with 

> sudo gedit /boot/grub/menu.lst



> title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=cb8927de-1b14-4e53-b4e3-d64c000bcc7d ro quiet splash locale=fr_FR
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

should looks omething like this after depending on your kernel. (just remove the break=top that you added before and for all kernels that have it there!)

cheers

---

### Post by bighead0618 on 2007-09-22
GREAT!!! thx...

Yeah.. now I see it in the thread.. Like page 3 or 4.. I must have missed it... 

its been a long day trying to get everything working... my next task is to see if my wireless network works and if i can hibernate!!

thanks again!

---

### Post by saru411 on 2007-09-23
what wireless do you have? if dell 1390 then use this thread. its as easy as click and its done!

[http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom+1390](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom+1390)

---

