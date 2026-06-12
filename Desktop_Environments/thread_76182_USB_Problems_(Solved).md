---
title: "USB Problems (Solved)"
date: 2005-10-14
forum: Desktop Environments
---

### Post by steven6817 on 2005-10-14
I have installed Ubuntu 5.10 on my Compaq Presario R3000 (512 ram, 60 g hard drive, amd Atmlon XP 2800, nVidia nForce3 USB,) sense the development started but my 128m Lexar JumpDrive stopped working after i upgraded to the final version.  I love Ubuntu and have installed it on 2 other machines but if my jumpdrive does not work I can not transfer my reports from my work laptop to my at home workstation.

thanks,

Steven6817

---

### Post by Ampersand on 2005-10-14
Try typing 

```
dmesg | tail 
``` 

in Konsole a few seconds after plugging in your usb drive. This should say the location of the drive, or if there's been a problem detecting it.

Also, try logging in to Gnome if you have it installed. The drive should appear on the desktop when plugged in.

---

### Post by steven6817 on 2005-10-14
I entered "dmesg | tail " and got the posted screenshot,
do i need to install Gnome as i am running KDE?:confused:

---

### Post by Ampersand on 2005-10-14
The gnome idea was optional, no need to install anything extra if you've not got it already.

Check whether it's been mounted to a folder in /media. If it hasn't, try making the folder '/media/usb' (sudo mkdir /media/usb) and then try mounting it manually:

```
sudo mount -t vfat /dev/sda1 /media/usb
```

---

### Post by 11hjpphty76lkjj on 2005-10-14
In theory the following steps might fix your problem:  Althought I could be incorrect.

remove usb device
terminal
sudo gedit /etc/fstab
add line:
/dev/sda               /mnt/jumpdrive         vfat    rw,user,auto   0  0
save exit
cd /media
sudo mkdir jumpdrive
chmod 777 jumpdrive (could be optional..)
sudo mount -a
exit terminal
plug in device
pray
use your gui as usual to access the usb device

Aaron

---

### Post by Stormy Eyes on 2005-10-14
**kalosaurusrex**, where's the step that involves inventive uses of profanity? :)

/used to have problems hooking up his iRiver H320 music player.

---

### Post by steven6817 on 2005-10-14
thanks it worked!


Steven6817:)

---

### Post by 11hjpphty76lkjj on 2005-10-15
The inventive use of profanity is step 1. :D 

Aaron

---

### Post by aysiu on 2005-10-15
[QUOTE=steven6817]thanks it worked!


Steven6817:)[/QUOTE] I know your problem's been solved already, but you may find [this thread](http://www.ubuntuforums.org/showthread.php?t=74541) a useful peek as well. I think it's a common bug. I've seen complaints about it in the Kubuntu forums as well.

---

