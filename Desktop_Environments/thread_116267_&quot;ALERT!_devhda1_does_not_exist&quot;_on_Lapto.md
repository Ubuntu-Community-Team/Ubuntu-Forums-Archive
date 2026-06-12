---
title: "&quot;ALERT! /dev/hda1 does not exist&quot; on Laptop"
date: 2006-01-12
forum: Desktop Environments
---

### Post by Phuzion on 2006-01-12
I have just purchased an Acer TravelMate 4402WMLi.  It is a Turion 64 system.  It came with a 'virus' loaded on it (Proprietary Acer WinXP) so I wanted to remedy the situation and install Ubuntu as quickly as possible.  I did a low-level quick format on the 100GB HDD and went through the set-up for 32bit Ubuntu Breezy Badger 5.10.  / was 20GB Ext3, swap was 2GB (system has 1GB of DDR) and a /home directory of 70GB Ext3.  Made the root volume the bootable and all the status icons are 'happy faces', wrote changes to disk.  The distro finished installing and rebooted.  As soon as Grub finishes initializing the kernel, I receive "ALERT! /dev/hda1 does not exist  Dropping to shell".

I tried the same procedure with the 64bit Ubuntu CD and received the same result.  I go back into the set-up, each time, and everything looks good.  I let the partitioner set-up my rive and it does the same thing.  Could thi be a controller issue?  I checked various forums, how tos and read up on what this error means to GRUB but I haven't found anything helpful (I am not even trying to dual-boot).

I am going to continue to work on this but if anyone has any immediat experience with a similar issue, I would like to know what you did to resolve it.

Thx

"End of Line" - MCP

---

### Post by dcstar on 2006-01-12
[QUOTE=Phuzion]I have just purchased an Acer TravelMate 4402WMLi.  It is a Turion 64 system.  It came with a 'virus' loaded on it (Proprietary Acer WinXP) so I wanted to remedy the situation and install Ubuntu as quickly as possible.  I did a low-level quick format on the 100GB HDD and went through the set-up for 32bit Ubuntu Breezy Badger 5.10.  / was 20GB Ext3, swap was 2GB (system has 1GB of DDR) and a /home directory of 70GB Ext3.  Made the root volume the bootable and all the status icons are 'happy faces', wrote changes to disk.  The distro finished installing and rebooted.  As soon as Grub finishes initializing the kernel, I receive "ALERT! /dev/hda1 does not exist  Dropping to shell".
.......[/QUOTE]
This may be of some value, (it seems to be a known problem):

[http://groups.google.com.au/group/linux.debian.bugs.dist/browse_thread/thread/4829d95465fdd83a/ed8fdba35bf7f265%23ed8fdba35bf7f265?sa=X&oi=groupsr&start=2&num=3](http://groups.google.com.au/group/linux.debian.bugs.dist/browse_thread/thread/4829d95465fdd83a/ed8fdba35bf7f265%23ed8fdba35bf7f265?sa=X&oi=groupsr&start=2&num=3)

---

### Post by ahave2005 on 2006-01-13
I have the same problem, when I reboot my laptop. I have to turn it off, before starting it again, and it boots fine then.
/ahave

---

### Post by Phuzion on 2006-01-13
Thanks guys.  I am going to try each, now.  I will let you know.

---

### Post by _fantom_ on 2006-01-14
i'm having the same/similar problem

i'm trying to install on an extrnal hard disk

when it reboots after instalation, as soon as i see the ubuntu logo on the screen, i get:

Alert! /dev/sda1 does not exist. Dropping to a shell 

and ...

/bin/sh can't access tty; job control turned off

typing "help", i get a list of commands, but i don't know what to do whith them :( it's my first time with linux

can anybody tell me step by step, how to fix this problem? :???:

---

### Post by Phuzion on 2006-01-14
I have resolved my problem.  I will, very briefly, describe the steps I took but my advice is, wait for Dapper.

I edited my hda with the SysRescueCD using:

fdisk /dev/hda

Enter m for menu options.  I created 3 partitions hda1(2)(3).  I then used qtparted to format the partitions root / Ext3, swap and /home Ext3.  I then used the fdisk again to make the root partition bootable.

So, I manually set-up my partitions before installing Ubuntu.

I used the install CD, Breezy Badger 5.10 and when it loaded the partitioner module.  All the labels were wrong but the file systems were intact.  I changed the labels to "/" and "/home", swap was ok.  Wrote changes and installed fine but I STILL received the same error mesage on reboot.  I tried everything I could think of and I am only a slightly knowledgable newbie, so, finally, I cheated.

I checked my partition tables with the SysRescueCD and they were still intact.  I browsed the root partion and Ubuntu installed fine, all files and directories were in the root /.  I then created a directory in /home called 'hd'  - /home/hd.  I then mounted the /dev/hda to /home/hd.  Then, with the help of a friend, I was able to change the root access from the live cd to /home/hd/bin/bash.   Now I had root access to my Ubuntu install.  I modified apt to include multiverse universe backports.  I tried to update apt but it wanted me to insert the install CD and as anyone who has ever used a Live CD should know, the CDROM was locked so I used vi to text edit apt sources list from looking at the CDROM and added all the lines needed to update everything over the internet, including breezy-backports.  Due to my inexpeience with vi, i had copies of the aptsource list in ram and it couldn't access the file- rebooting resolved this.  I recreated the /home/hd, mounted hda and did the chroot process again.  Updated apt and then used apt to do a dist-upgrade, the next reboot worked fine but had to re-install ubuntu desktop because of errors (mine stopped at 5% of the initial boot configuration that runs on first boot-up.  It took awhile to upgrade and then to re-install the ubuntu desktop but it worked, in the end.  Now it boots everytime.

If you can follow what I did, you should be ok.  Good luck though, it was allot of trial and error and research (the newbie, i am).  I thought about making a Wiki for it but I do not think this is a fix, this is a get-by method.  I suppose if you just updated the initramfs-tools, that would work?

Brian

---

### Post by _fantom_ on 2006-01-17
I really appreciate your effort to explain Phuzion, but to be honest, i did not understand much :( i'm ultra newbie to linux

Maybe there is an alternative &#8220;easy way&#8221; (?) ;) 

in-between, i did install mandrake, but now i have a problem to make my modem work ](*,) 

thanks for your reply, regards from Greece :)

---

