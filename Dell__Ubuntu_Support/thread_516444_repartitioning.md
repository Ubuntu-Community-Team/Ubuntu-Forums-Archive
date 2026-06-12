---
title: "repartitioning"
date: 2007-08-03
forum: Dell  Ubuntu Support
---

### Post by mymyheyhey on 2007-08-03
Ok, I'm using a Dell 6400 which came with WinXP, I eventually managed to wipe it I then installed Ubuntu Feisty onto it.

Now however I want to duel boot it with XP and when repartitioning im having this error.

Check file system on /dev/sda1 for errors and (if possible) fix them.

Any suggestions on what im to do?

---

### Post by benx009 on 2007-08-03
> **mymyheyhey said:**
> Ok, I'm using a Dell 6400 which came with WinXP, I eventually managed to wipe it I then installed Ubuntu Feisty onto it.

Now however I want to duel boot it with XP and when repartitioning im having this error.

Check file system on /dev/sda1 for errors and (if possible) fix them.

Any suggestions on what im to do?

wait, you said you wiped windows from your pc, but want to dual-boot feisty with it.  is windows on your pc or not?  if you have completely gotten rid of xp on your system, there is no way to boot it up again.

---

### Post by mymyheyhey on 2007-08-03
> **benx009 said:**
> wait, you said you wiped windows from your pc, but want to dual-boot feisty with it.  is windows on your pc or not?  if you have completely gotten rid of xp on your system, there is no way to boot it up again.

The XP on it had all of dells rubbish installed, I wiped it to install Feisty.

I now have one big partition which I want to split up to put XP onto one and then duel boot.

---

### Post by ubun on 2007-08-03
I did some research on dual boot and came across this excellent tutorial on LinuxDevCenter before installing Ubuntu that really helped me.

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

I did this on my Dell Dimension desktop so had a little flexibility of having multiple physical hard disks. The live CD installed GRUB by default in the MBR without giving me any options (may be a first timer error too....) but have had absolutely no problems at all. I was told in one of these tutorials that its easy to install Ubuntu over existing XP and create a dual boot instead of the other way around.  Others please correct me here if I am wrong. I guess WinXP is not very "Other OS" friendly. If it is true then I would first install XP and then Ubuntu but then again that is something a non-geeky person like me would do it. Advanced users may have other opinions.

---

### Post by deserthowler on 2007-08-03
> **ubun said:**
> 
I did this on my Dell Dimension desktop so had a little flexibility of having multiple physical hard disks. The live CD installed GRUB by default in the MBR without giving me any options (may be a first timer error too....) but have had absolutely no problems at all. I was told in one of these tutorials that its easy to install Ubuntu over existing XP and create a dual boot instead of the other way around.  Others please correct me here if I am wrong. I guess WinXP is not very "Other OS" friendly. If it is true then I would first install XP and then Ubuntu but then again that is something a non-geeky person like me would do it. Advanced users may have other opinions. 

There are other ways but you did the easiest by far.  Grub will handle the XP system automatically (usually).  Don't bother to do the updates on XP until you get Ubuntu installed.  That will save you a lot of time downloading in case the Ubuntu install breaks something.

The whole dual boot thing is pretty well ironed out and there isn't any problem for the most part.    Something can always happen, but then a meteorite could come through the roof and really mess up your install too.

I once had a system with Win98 and Win2K installed in a dual boot.  I then installed Linux in the third partition and had 2 choices on the grub menu, Windows and Linux.  If I clicked on Windows, it would give me the 98/2K boot menu.  Everything worked flawlessly with no intervention on my part.

Earl

---

### Post by mymyheyhey on 2007-08-04
No offence to you guys, but doesn't help my problem?

---

### Post by deserthowler on 2007-08-04
Ok, then this might help.  Partition your drive into 2 partitions first.  I use gparted for this.  Install XP on the first partition and Ubuntu on the second.  You don't need to format the partitions.  I don't know if XP do the partitioning or not.

Earl

---

### Post by mymyheyhey on 2007-08-04
....
I wasn't asking how to do it.

Read my  first post again and then answer if you can help.

---

### Post by deserthowler on 2007-08-04
If I understand correctly, you have Feisty installed and want to make your disk into 2 partitions, one for XP and one for Feisty.  You are trying to make these partitions with XP. 

XP won't recognize your hard drive because you have Linux installed and Windows doesn't recognize non-windows partitions.  

If that is your situation, you have to wipe out the Linux install with something like gparted and make 2 partitions first.  You can leave them blank.  If this isn't your situation, I am misunderstanding the whole situation and am sorry about that.

Earl

---

### Post by HermanAB on 2007-08-04
Nope, I won't do any of the above!

Rather go to the VMware web site, get VMware server, install that and install XP inside VMware.  It is much more convenient to run Windows concurrently with Linux than to dual boot.

There is also another reason: If you install Windows after Linux, then Windows will bork your master boot record.  Windows doesn't play well in groups!

Cheers,

Herman

---

### Post by deserthowler on 2007-08-04
That is what I did with Win2K and Virtual Box on my Ubuntu install.  It works great.

Earl

---

### Post by HermanAB on 2007-08-04
For raw speed under emulation, Win98 SE is even better and it can run almost all XP applications.

---

