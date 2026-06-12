---
title: "Want to go to clean install of Kubuntu from Ubuntu"
date: 2008-02-10
forum: Desktop Environments
---

### Post by guitardude on 2008-02-10
Right now my setup is as follows:
120 gig internal drive:
Partition 1: Created by my laptop's manufacturer. it is a Vista Recovery partition
Partition 2: Microsoft Windows Vista Home Premium 32 bit
Partition 3: Ubuntu Gutsy
Partition 4: Linux Swap

I want to go to Kubuntu. I know that you can just do the desktop thing through synaptics but i want to clean install it. I am using the GRUB bootloader, so i am assuming that my Vista bootloader has been overwritten. What would be my best course of action? Deleting the Ubuntu and Swap partitions and leaving them as unallocated space, or just booting to the Kubuntu Live CD and doing an install through there with the Ubuntu Partitions still on the drive and try to overwrite them in the install process. Will i need to set up the vista bootloader before i do this just incase i cant get it to work because i would then need to get back into vista (i dont have a vista cd, it was pre-installed). Also, does Kubuntu use the GRUB bootloader? I kinda like it :-) Thanks in advance,
guitardude

---

### Post by TeaSwigger on 2008-02-10
No worries :) You're correct, just use the Kubuntu CD and install it like you did with the Ubuntu CD. In setting up the partitions, use "manual". You can delete the Ubuntu partition, installing Kubuntu in its place, keeping the rest. You'll see how to tell it to use the existing swap partition during the paritioning set up. This won't bother Vista and yes, Kubuntu also uses GRUB. :)

---

### Post by guitardude on 2008-02-10
Thanks a bunch!  :-)
guitardude

---

### Post by tnd on 2008-03-21
Hi, I've got exactly the same problem so this thread's been really helpful, thanks :)
EDIT: I was confused. I'll start another thread...

---

