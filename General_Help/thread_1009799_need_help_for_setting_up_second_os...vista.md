---
title: "need help for setting up second os...vista"
date: 2008-12-13
forum: General Help
---

### Post by ultratek on 2008-12-13
I just formatted my xps420 and installed ubuntu 

i left about 90 gigs of unallocated space to re-install vista as a second os so i can play crysis=)

well when i boot from the vista cd to install vista i come to a installnow button... iam afraid to go anyfurther in fear that i wont have a chance   to partition that unallocated space i reserved for vista and choose it to install vista on....

can anyone help me..i dont want to mess up my linux setup...thanx=)

---

### Post by TeXtonyx on 2008-12-13
Run sudo fdisk -l  which will tell you what partitions that Ubuntu
is using. sda1 should be the ext3 type 83 Linux partition and you
should have one for swap. When you install Vista just make sure
that you install it into the unallocated space, not a partition.

Vista will install its own bootloader to the MBR. So you have to 
reinstall grub again so that its bootloader controls the MBR.
This can be done with the Ubuntu live cd, or Super Grub Disk.

From the Ubuntu live cd terminal command line:
sudo grub
grub> find /boot/grub/stage1
grub> root (hd0,0) use the partition that the find command reports.
grub> setup (hd0)
grub> quit

When you reboot, you should have the grub boot option menu back.
If Vista isn't on it, then add Vista to menu.lst under other OS
gksudo gedit /boot/grub/menu.lst  
Scroll down to the example which looks something like this, 
title Windows Vista/Longhorn (loader)
root (hd0,4)
savedefault
makeactive
chainloader +1

The part you need to get right is the  root (hd0,4)
The 4 is the number of the partition Vista is installed on.

But this is just an example because I don't know what the correct
partition number. Run sudo fdisk -l
and it will tell you which partition is ntfs which equals Vista

If it says sda5 that equals (hd0,4)<---grub entry in menu.lst
If it says sda4 that equals (hd0,3)<---grub entry in menu.lst

because the sda partition number (the 4 and 5 above as in sdax)
is one number higher than what you use for the grub entry.
Then sda = hd0 and next the partition number, then sda1 = (hd0,0)
then sda2 = (hd0,1)  , then sda3 = (hd0,2)
These are examples, the right number comes from sudo fdisk -l
which report sda and then the partition number next after sda

---

### Post by ultratek on 2008-12-13
wow thanks for the reply..

well i went to install vista doing as you said it gave me the optionto select the unallocated space and partition it and format it...

but it would not move on using the next button saying windows could not find a system disk/config suitable enough for installation... something like that..

---

### Post by deadned on 2008-12-13
I doubt this helps you much now, but Vista comes with a partition editor. When I first installed Vista and Ubuntu, I installed Vista first, created an empty partition, and then installed Ubuntu. It was a piece of cake.

---

### Post by TeXtonyx on 2008-12-13
> **ultratek said:**
> wow thanks for the reply..

well i went to install vista doing as you said it gave me the optionto select the unallocated space and partition it and format it...

but it would not move on using the next button saying windows could not find a system disk/config suitable enough for installation... something like that..


[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

How to dual-boot Vista with Linux (with Linux installed first) 
-- the step-by-step guide with screenshots 

When you get Vista installed it might be a good idea to install
Vista SP1, Service Pack 1, before reinstalling grub.

---

### Post by ultratek on 2008-12-13
i let ubuntu boot up on the cd and ran the terminal..
is this where i run the cmds?...the cmds are not working

---

