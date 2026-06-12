---
title: "New iPod setup"
date: 2006-07-22
forum: Desktop Environments
---

### Post by gotmonkey on 2006-07-22
I just received my new (refurbished) ipod 20gig w/Clickwheel yesterday and I am trying to set it up in linux.

when I plug in the ipod it shows up on my desktop.

When I run fdisk -l it returns this

Disk /dev/sda: 20.0 GB, 20000268288 bytes
64 heads, 32 sectors/track, 19073 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

Disk /dev/sda doesn't contain a valid partition table

I have gtkpod installed and I can't seem to do anything else.
It seems that I need to format the ipod but I am not sure how to and I haven't been able to find what I need in the forum.

I can't install it on my windows box. Those dorks at apple only sent me a firewire cable and my windows machine doesn't have firewire. The only machine with firewire is my ubuntu machine. 

Could someone lend a hand.

---

### Post by mlind on 2006-07-22
I thinkt it should contain two partitions by default, one for firmware, one for your stuff.

Did you type fdisk -l, or fdisk -l /dev/sda ?

I was using windows when I setup my ipod, but there was some formatting included that Apple's ipod updater did.
I'm not much of help here, but you could try running windows on vmware to get the ipod firmware updater to work.

---

### Post by llamakc on 2006-07-22
Do you have the kernel modules loaded for that filesystem support? Is it a "Windows-ready" iPod or an Apple one? Maybe you need to install hfsplus from apt/synaptic?

---

### Post by Dubbayoo on 2006-07-22
Does it even have a usb port? If so I would get a usb cable to make life easier. 
You need it formatted to fat32 for Linux which I imagine you can do fine with gparted; apt-get it. I'm not positive you have to do this though. Try just dragging a file to it using gtkpod and see what happens. 
I have a 4GB Nano that appears unformatted in gparted but it actually has 680 songs on it and works fine. 

steve@ubu:~$ mount | grep ipod
/dev/sdc2 on /media/ipod type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1001,gid=1001,umask=077,iocharset=utf8)
steve@ubu:~$ du -s /media/ipod/
3.7G    /media/ipod/
steve@ubu:~$ ll /media/ipod/
total 28K
drwx------  2 steve steve 4.0K 2000-01-04 04:08 Calendars/
drwx------  2 steve steve 4.0K 2006-06-16 20:29 Contacts/
drwx------  6 steve steve 4.0K 2005-08-18 17:45 iPod_Control/
drwx------ 18 steve steve 4.0K 2006-04-20 23:19 Music/
drwx------  2 steve steve 4.0K 2000-01-04 04:08 Notes/
drwx------  3 steve steve 4.0K 2006-05-21 00:44 Photos/
-rwx------  1 steve steve  296 2006-04-20 23:19 WMPInfo.xml*

---

### Post by Dubbayoo on 2006-07-22
Does it even have a usb port? If so I would get a usb cable to make life easier. 
You need it formatted to fat32 for Linux which I imagine you can do fine with gparted; apt-get it. I'm not positive you have to do this though. Try just dragging a file to it using gtkpod and see what happens. 
I have a 4GB Nano that appears unformatted in gparted but it actually has 680 songs on it and works fine. 

steve@ubu:~$ **mount | grep ipod**
/dev/sdc2 on /media/ipod type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1001,gid=1001,umask=077,iocharset=utf8)
steve@ubu:~$ **du -s /media/ipod/**
3.7G    /media/ipod/
steve@ubu:~$ **ll /media/ipod/**
total 28K
drwx------  2 steve steve 4.0K 2000-01-04 04:08 Calendars/
drwx------  2 steve steve 4.0K 2006-06-16 20:29 Contacts/
drwx------  6 steve steve 4.0K 2005-08-18 17:45 iPod_Control/
drwx------ 18 steve steve 4.0K 2006-04-20 23:19 Music/
drwx------  2 steve steve 4.0K 2000-01-04 04:08 Notes/
drwx------  3 steve steve 4.0K 2006-05-21 00:44 Photos/
-rwx------  1 steve steve  296 2006-04-20 23:19 WMPInfo.xml*

---

### Post by gotmonkey on 2006-07-23
I installed qtparted and this is what it shows. I did try running gtkpod and adding files to the errors, but got errors.

I think the question is now, do I format all of the partions in fat32?

---

