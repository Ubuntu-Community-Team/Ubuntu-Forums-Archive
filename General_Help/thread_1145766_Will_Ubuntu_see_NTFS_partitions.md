---
title: "Will Ubuntu see NTFS partitions?"
date: 2009-05-01
forum: General Help
---

### Post by GL_NORWAY on 2009-05-01
If I have Ubuntu and plug in a NTFS external HD or USB-pin, will Ubuntu be able to read that partition and copy files to and from it?

---

### Post by mkoehler on 2009-05-01
It should, so long as you have the ntfs-3g package installed from synaptic.

---

### Post by PhilMize on 2009-05-01
Yes ubuntu will see it. Though make sure you have safely removed it from a windows machine before you plug it into a ubuntu machine. If it's not safely removed it won't mount.

---

### Post by jbrown96 on 2009-05-01
absolutely. The only problem that you may have is if you don't "safely remove" the disk from windows. If a NTFS drive is not unmounted correctly, then it marks itself as dirty. Ubuntu is very cautious and doesn't like to mount dirty volumes, so you will get an error. 

You can fix the problem one of two ways.

1) Force mount
you will need to mount the volume from the terminal. 
A) open a terminal. apps-->acc-->terminal
B) ```
sudo fdisk -l
``` this will list all your devices. Find your external drive. you can tell because the sizes are listed. You are looking for something like /dev/sdb1 or /dev/sdc2. you will need this for the next step.
C) Create a directory to mount it. I like to always have a folder on my desktop called mount that I use to mount various things (usually network file shares). You can create it by right clicking on your desktop. You can name it whatever you want, but I'm going to call it mount, so just replace mount with whatever you name it
D) mount it. ```
sudo mount /dev/sdb1 ./Desktop/mount
``` replace sb1 with what you found in step B and mount with what you found in step C

2) Cleanly remove it from windows.
A) Boot into windows
B) Safely remove it


You will never have these problems if you safely remove the drive from windows (or reboot without removing it). I just put these instructions on there, so that if you have a problem, you don't freak out.

---

### Post by RealG187 on 2009-05-01
> **PhilMize said:**
> Yes ubuntu will see it. Though make sure you have safely removed it from a windows machine before you plug it into a ubuntu machine. If it's not safely removed it won't mount.

Well you can force a mount...

---

