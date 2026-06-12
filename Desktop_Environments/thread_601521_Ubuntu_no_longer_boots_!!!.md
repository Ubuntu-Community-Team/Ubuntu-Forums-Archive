---
title: "Ubuntu no longer boots !!!"
date: 2007-11-03
forum: Desktop Environments
---

### Post by Hagar55 on 2007-11-03
I tried to solve the long boot bug by changing the usplash.conf file as described in another part of this forum.

I reboot to see if it works and find I can nolonger boot into Ubuntu.

At the grub login screen I get two options:
Ubuntu 7.10 kernel 2.6.22.14- generic and
Ubuntu 7.10 kernel 2.6.22.16-generic and offcourse recovery mode for both of these.

I have to confess I always booted the first option kernel 2.6.22.14 (don't know if that is the problem.

When I try to boot now I only get this message:
Kernel Panic - not syncing: VFS Unable to mount root FS on unknown block (0.0)

Is this because of the change I made to usplash.conf ??
Or did something else go very wrong ?

When I trie to boot into kernel 2.6.22.16 it starts to boot then goes to a text screen, flickers a few times and then dies.

right now I'm very glad I installed Ubuntu in a dual boot configuration (WinXP)....

I really would like some advice on this.

---

### Post by Happy_Man on 2007-11-03
Yeah, it probably is the change you made to usplash.conf. Undo that change and try again.

---

### Post by Hagar55 on 2007-11-03
How do change it back when I can't boot into Ubuntu, Windows doesn't read those partitions...

So I use the lice cd ?,
How do I acces that file with the right permission ?

---

### Post by Happy_Man on 2007-11-03
From Windows, you can install drivers that will allow Windows to read Linux partitions. They are available at [http://fs-driver.org](http://fs-driver.org) .

---

### Post by Hagar55 on 2007-11-04
Ok I tried a few things, the drivers for windows don't help me because I don't have the file permision to change the file and they don't read the partitions correctly (windows only wanted to format them).

I tried booting into rescue mode with an Ubuntu 7.04 CD and that just ended with a black screen.
I can start Ubuntu from live cd with an Ubuntu 7.04 and Kubuntu 7.10, but then I don't have the rights to the drive to change the file.

I cannot boot up the live CD with Ubuntu 7.10, then I get a dark screen ??

Does booting from a lice CD with 7.10 interact with the 7.10 that is installed ?( It's an upgraded version of 7.04)

When I boot up in recovery mode in Kernel 2.6.22.16 I get a command line with root and my user name.
Can I go from there to change back the usplash.conf file ?

To recap I changed the resolution in the usplash.conf file to my native screen resolution (1280*1024) and then ran the following command : sudo update-usplash-theme usplash-theme-ubuntu

Is there a chance I can fix this or should I try to reinstall.
If so since I cannot seem to boot from the 7.10 live CD (I downloaded it twice from different locations and burned it on separate cd's ....no avail), should I reinstall 7.04 and then upgrade again.

If I reinstall is there a way I can reuse the home partition with the files that are under my current user name ?

---

### Post by warpyb1 on 2007-11-11
Hi All, 

I have the same problem however all I have done is update my system to the newest version of Kubuntu!  I ran it last night after the adept installer said that I had over 1000 updates to compelte.  It got half way through then failed saying that some of the updates would break dependencies on my machine and so it finished and that was it adapt closed down and I was left with the machine working I asume with the same kernal version which I think is 14 although not 100%.  I am a lynix newb so Im still working my way aorund everything. 

This morning when I started my system with the new version of the kernal I get a kernal panic message and the system fails to boot.  When I try the other 2 versions stored in GRUB I can get in to the O/S however, things have changed my login screen is different and there seems to be loads of new apps installed on my machine.  With almost all of them failing to work. 

The network manager has been updated I seem to hve Wine now MSN is new and I am unable to find my KDE wallet to start my wireless as it used to prompt me for a password when it booted. 

Help!!  How on earth can I go back to my previous working version of Kubuntu??  Or is there anyway I can reinstall the new version of the kernel and associated updates so that I can continue with the new version of Kubuntu. 

Please help me.   Of one other thing when I get back in to my previous version of the O/S the adapt manager fails to load and I get prompted with a message saying that the database is locked and would I like the manager to try and unlock itself, which it trys then crashs out.  So I really am stuck.

I remember having this problem some time ago and after doing a search there was some code that I ran which unlocked the manager however im not sure if this is going to help nor can I remember what the code was that unlocked the manager. 

Your help would be so appreciated

Thank you.

---

### Post by Happy_Man on 2007-11-11
Yeah... as a general rule, even though the system lets you "upgrade" to a new version (eg Feisty to Gutsy), never take it up on its offer. All it ever does is completely break the system. Always do a fresh install of a new version. If you don't have a separate /home partition, please get oine now using the link in my signature. For now, though, I would suggest a backup and reinstall.

---

