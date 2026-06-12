---
title: "Installed NVIDIA driver 190, broke xserver"
date: 2009-12-12
forum: Desktop Environments
---

### Post by uranazo on 2009-12-12
Ok, so heres the basic rundown of what I've done to screw up my system...
My system is running dual NVIDIA 8600 GT 512's

Several times I've tried installing the NVIDIA proprietary drivers and it has failed every time. I used the GUI to install it in System->Administration->Hardware Drivers to update the driver and it installed fine with no errors.
When I reboot, i get the "kinit: no resume image, doing normal boot" line and into the shell prompt I go... Fixing it after installing using the GUI is quite easy as I've learned through a lot of research online, I simply did sudo apt-get remove dkms (or maybe dpms? cant remember) and the entire NVIDIA driver is gone, restart and xserver is up and running fine...

So in trying a different approach, I downloaded the driver directly from NVIDIA and ran it in tty1 and rebooted...

Now, I can't get rid of the NVIDIA driver! Package dkms, nvidia-settings, nvidia-glx are not installed (I guess since I installed using the NVIDIA script?)...

It gets worse...

I read online on the NVIDIA that the biggest cause of the driver failing is conflict with the original xserver and that it should be removed before installation...

so i removed it, now there are, as best I can tell, no traces of nvidia drivers nor xserver on my machine... even when i rerun the nvidia driver dpkg -l nvidia shows no packages matching nvidia... 

How can I get xserver back up?

---

### Post by fancypiper on 2009-12-12
Have you tried this yet?

# Reconfigure X
sudo dpkg-reconfigure xserver-xorg

---

### Post by uranazo on 2009-12-12
yes, it builds an xorg.conf with nothing in it...


is there a way to reinstall xserver from a live cd or from the command line?

---

### Post by fancypiper on 2009-12-12
Try:
sudo apt-get install xserver-xorg-core

---

### Post by uranazo on 2009-12-12
If I have any typos sorry, I have to type everything from my computer to my laptop because I can't get internet in the live session but here is what my current xorg.conf is, I'm using the failsafe...

Section "Device"
              Identifier             "Configured Video Device"
              Driver                  "vesa"
              Option                "UseFBDev"                     "true"
EndSection

Section "Monitor"
              Identifier             "Configured Monitor"
EndSection

Section "Screen"
               Identifier                "Default Screen"
               Monitor                  "Configured Monitor"
               Device                    "Configured Video Device"
EndSection

---

### Post by uranazo on 2009-12-12
The problem is when I log into tty1, I have no internet connection... Everytime I try to do a "sudo apt-get install" it always immediately says "Could not resolve address ..." This happened before when I installed the NVIDIA driver using the Ubuntu GUI... Internet was fixed when I removed the nvidia package... But now that I've installed using the NVIDIA script, I am not entirely sure its gone plus xserver is gone...


So I need a way to reinstall xserver using the cd, either from a live session or from the tty1 terminal accessing the cd....

---

### Post by fancypiper on 2009-12-13
If you have internet connection with the live CD, you should be able to do it. 
```
# DANGEROUS! ENTER COMMANDS EXACTLY!
mount /dev/sdb2 /mnt #<--Change to your root partition
mount /dev/sdb1 /mnt/boot #<--If you have a /boot partition
mount -o bind /proc /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt bash
sudo apt-get install xserver-xorg-core
exit
```

Reboot and see if it worked.

---

### Post by uranazo on 2009-12-13
I can't get an internet connection in the live session...

is there a way to install it directly from the CD? the cd must have the xserver package on it right?

---

### Post by fancypiper on 2009-12-13
{Slaps forehead} Try booting to the live CD, mount your / partition and copy the /etc/X11/xorg.conf to the /etc directory of the mounted /.

---

### Post by uranazo on 2009-12-13
yeah i did that but there is no xserver for the xorg.conf  ...

I need to get it off the cd... is there a way to do this with dpkg?

---

### Post by uranazo on 2009-12-13
this is what my xorg.conf is from the live cd, its pretty generic, i know i've seen it with more information inside it:

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

---

### Post by fancypiper on 2009-12-13
BTW, what Ubuntu release are you running?

I searched the forum and found this: [xorg.conf](http://ubuntuforums.org/showthread.php?t=1300440) Scroll down to post#20. Just boot the live CD, mount / and delete the xorg.conf file.

---

### Post by uranazo on 2009-12-13
I have 9.04

ive done that, i need to undo this command without an internet connection:
```
sudo apt-get remove xserver-xorg-core
```

basically, I need to do
```
sudo apt-get install xserver-xorg-core
```

but that wont work because there is no network connection

What is the equivilant for installing from the cd instead of the internet?

---

### Post by uranazo on 2009-12-13
i think im done for, warning to all, **[SIZE="5"]NEVER INSTALL THE NVIDIA DRIVER![/SIZE]**

I'm just gonna have to reformat... really pathetic, the damn xserver package is on the cd in my hand, and there is no way to get it off and installed...


This is entirely NVIDIA's fault btw, I have yet to see a driver they've produced work in linux, my last video card had problems and so does this one...

---

### Post by uranazo on 2009-12-13
ok odd thing, if anyone is reading this....

I went to reinstall ubuntu from the cd while running the live version and then when I restarted, all my settings, files and everything were on my desktop when I booted back up... I'm guessing this happened because I installed over top of my original install, with the exact same size and all and I didn't check off the format box, so anything that was missing or corrupted was overwritten.... Its like it repaired it? Only problem is now, I have no wireless lan card so I have no internet still...

I have the RTL8187, how can I get it to recognize it?

---

