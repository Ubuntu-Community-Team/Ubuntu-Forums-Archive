---
title: "I deleted grub, can i install grub2?"
date: 2009-03-08
forum: General Help
---

### Post by dragos240 on 2009-03-08
Okay, so my grub folder is gone, i am still in ubuntu though, i wish to install grub 2, how would i go about doing this? I really want to get grub2 on bootup, because of the new 24bit colors. Can anyone help me please?

---

### Post by dragos240 on 2009-03-08
Please reply :'(

---

### Post by LegendofTom on 2009-03-08
Have you tried "sudo apt-get install grub2"

---

### Post by dragos240 on 2009-03-08
> **LegendofTom said:**
> Have you tried "sudo apt-get install grub2"

Would that be different than doing to the synaptic manager and installing grub2 that way?

EDIT: It just created 2 files, one blueish walpaper of the debian logo, and a unicode file.

---

### Post by tommcd on 2009-03-08
> **dragos240 said:**
> Would that be different than doing to the synaptic manager and installing grub2 that way?

EDIT: It just created 2 files, one blueish walpaper of the debian logo, and a unicode file.

There is no difference in using apt-get or synaptic to install packages. Synaptic is a GUI  front end for apt-get.

I don't think grub 2 is considered stable yet. I would stick with the grub that Ubuntu came with. You can reinstall grub from the live CD like this:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
There are splash images for grub:
[http://packages.ubuntu.com/intrepid/admin/grub-splashimages](http://packages.ubuntu.com/intrepid/admin/grub-splashimages)
You should be able to search for and install grub-splashimages from synaptic or apt-get.

---

### Post by dragos240 on 2009-03-08
thanks i'm going to try it.

---

### Post by dragos240 on 2009-03-09
No, not working. I can't reinstall grub using that method, it spits out that it can't find device for /boot or something. Will super grub disk work?

---

### Post by tommcd on 2009-03-10
> **dragos240 said:**
> No, not working. I can't reinstall grub using that method, it spits out that it can't find device for /boot or something. Will super grub disk work?

How are you booting Ubuntu then? Do you have grub installed currently?
Can you post the commands you used to reinstall grub? The method listed in the link I gave shoud work.

Yes, the Super Grub Disc does work well for reinstalling grub. Give it a try.

---

### Post by dragos240 on 2009-03-10
I have ubuntu installed, but i am using the ubuntu live cd, also i made a live cd of a grub backup, so for now, i can boot into ubuntu. But it's not permenent.

---

### Post by tommcd on 2009-03-11
I think I know what is wrong. If you deleted the entire grub directory in /boot, then reinstalling grub via the live CD may not work. 
Try booting from the Ubuntu live CD, open a terminal, and run:
```
sudo grub-install /dev/sda
```
If your Ubuntu is on a different hard disk than /dev/sda then change the command accordingly. This should install grub to the MBR. Then try following this again:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
If that does not work, grub can be installed with the alternate install CD like this:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
I think the live CD has an option to "rescue a broken system" also. I'm not sure about the latest live CD since I use the alternate CD. 
The Super Grub Disc should be able to reinstall grub also.

---

### Post by dragos240 on 2009-03-12
Okay i booted from the ubuntu 8.10 disk, and typed in that command, it gave me a message:

```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

Any seggestions tom?

---

### Post by tommcd on 2009-03-13
> **dragos240 said:**
> Okay i booted from the ubuntu 8.10 disk, and typed in that command, it gave me a 
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```
Any seggestions tom?
What did you do to loose the original grub? In your first post you said you deleted the grub folder. Why did you do that?  And did you delete anything else? If you deleted the grub folder to install grub 2, then it would have been much safer to simply rename it grub.bak or whatever. I don't think removing the grub folder would have been necessary in order to install grub 2 in the first place.

 I have about used up all my grub suggestions. Have you tried the Super Grub Disc? Have you tried the "rescue a broken system" method listed here on the alternate CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
There is also the System Rescue CD, which has lots of great tools and is able to reinstall grub:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by abybaddi on 2009-03-13
Tomccd is right you can install the grub using the live cd. I had done it many a times.
:lolflag:

---

### Post by dragos240 on 2009-03-13
> **tommcd said:**
> What did you do to loose the original grub? In your first post you said you deleted the grub folder. Why did you do that?  And did you delete anything else? If you deleted the grub folder to install grub 2, then it would have been much safer to simply rename it grub.bak or whatever. I don't think removing the grub folder would have been necessary in order to install grub 2 in the first place.

 I have about used up all my grub suggestions. Have you tried the Super Grub Disc? Have you tried the "rescue a broken system" method listed here on the alternate CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
There is also the System Rescue CD, which has lots of great tools and is able to reinstall grub:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)


yes i deleted the grub folder. The reason why is because i tried to install grub2 but it was on a chainloader and i couldn't figure out what files it added so i could reinstall it. I know, i should have asked..

---

### Post by adrian15 on 2009-03-18
I think that you can try:

```

sudo apt-get install grub

```
in your system ([Boot it from SGD](http://www.supergrubdisk.org/wiki/Howto_Boot_Linux_only) or chroot from a live cd).

If it complains about /boot device you might need to create a /boot/grub/device.map file.

adrian15

---

