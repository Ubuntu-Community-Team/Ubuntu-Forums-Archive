---
title: "It is a mystery... &quot;&gt;_&gt;"
date: 2009-05-05
forum: General Help
---

### Post by The_Lost_World on 2009-05-05
Seriously... this thing comes up with a new problem every time I try to install it. :confused:

In any case, I just downloaded, burned, and checked integrity thoroughly the new Ubuntu 9.04 Jaunty Jackalope. I've figured out all I need to know for manual install (because, of course, auto install is not working) and now I try to boot it on live CD to install it, and I get this after it loads:

```
Loading, please wait. . .

BusyBox v1.10.2 (Ubuntu 1:1.10.z-1ubuntu6 built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

Okay, so I got this the last time I tried to live boot Ubuntu on Hardy Heron. I waited and it didn't do anything then, so I typed "exit" and then it would live boot just fine. However, upon entering that command this time on Jaunty, I get this:

```
cp: cannot create '/root/var/log/':No such file or directory
mount: mounting /root/dev on /dev/. static/dev failed:No such file or directory
mount: mounting /sys on /root/sys failed:No such file or directory
mount: mounting /proc on /root/proc failed:No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg
```

Now, come on, is this thing going to have some sort of diabolical error that prevents me from FINALLY installing every time? :rolleyes:

---

### Post by The_Lost_World on 2009-05-05
Bump. Anyone have any info to give? :confused:

---

### Post by The_Lost_World on 2009-05-06
...bump.

---

### Post by dabl on 2009-05-06
Looks like a bad burn on the CD, probably.  Follow the procedure described in #1 on this:

[http://kubuntuforums.net/forums/index.php?topic=3099811.0](http://kubuntuforums.net/forums/index.php?topic=3099811.0)

---

### Post by jarrettm on 2009-05-06
Not a bad CD burn I think. I have this problem on a Compaq machine. The same CD checks out and boots on a Dell Vostro Laptop and an ancient Dell tower

---

### Post by The_Lost_World on 2009-05-06
Uh... isn't that for Kbuntu?

In any case, yea, I'll make a new disk...

---

### Post by dabl on 2009-05-07
> **jarrettm said:**
> Not a bad CD burn I think. I have this problem on a Compaq machine. The same CD checks out and boots on a Dell Vostro Laptop and an ancient Dell tower

If it is not a defective CD, then the problem is with the optical drive in the computer that is having the problem reading it.

@T-L-W -- there's no difference between the (K)(X)(Ed)ubuntus wrt the process of making a Live CD or Alternate Install CD.  :)

---

### Post by jarrettm on 2009-05-07
Same machine boots 8.10 (both Ubuntu and Xubuntu) fine.

casper.log gives the following...

unable to find a medium containing a live filesystem

---

### Post by sgosnell on 2009-05-07
The CD could be bad, or the CD/DVD drive could be bad.  Or there could be a conflict with the hardware on the laptop.  Proprietary laptops can be problematic.

---

### Post by bapoumba on 2009-05-07
It probably has more to do with improper detection of the drive:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/143958](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/143958)
I know this is an old bug. I ran into this (or close) with my son's computer. Hardy installed fine, Intrepid was a no go.. I had no time to try Jaunty yet.

---

### Post by The_Lost_World on 2009-05-07
> **dabl said:**
> If it is not a defective CD, then the problem is with the optical drive in the computer that is having the problem reading it.

@T-L-W -- there's no difference between the (K)(X)(Ed)ubuntus wrt the process of making a Live CD or Alternate Install CD.  :)
Well I hope my optical drive isn't defective! There's no way I could replace it. >_< It can play games and DVDs just fine BTW.

---

### Post by sgosnell on 2009-05-08
My money would be on a defective CD.  You can get one with a corrupt downloaded file, or through a bad burn.  Run the md5sum check on the original .iso, and if that checks, run the Check CD for Defects choice.  You said you've checked the integrity, but not how.  If you've already done all this, then I have no other suggestions.

---

### Post by Naiki Makuri on 2009-05-08
My laptop has this problem with Live USB jaunty...

---

### Post by jarrettm on 2009-05-08
1. I don't think it's the CD, it boots fine on three other machines. I have used the option to verify the CD successfully.

2. It may be failure to recognise the CD/DVD, although 8.10 (Ubuntu and Xubuntu) boot perfectly.

3. I tried the alternate CD and it all points to the CD/DVD not being recognised, despite initially being used for the boot. By hitting Alt + F2, cd /dev , find . | grep cd shows nothing.

4. The alternate disk prompts you to load additional CD drivers, this seems to look on the floppy.

5. The machine boots on 8.10 from its hard drive. If I insert the CD it automounts as /media/cdrom on /dev/scd0. When booted from the CD /dev/scd0 does not appear.

---

### Post by The_Lost_World on 2009-05-08
> **sgosnell said:**
> My money would be on a defective CD.  You can get one with a corrupt downloaded file, or through a bad burn.  Run the md5sum check on the original .iso, and if that checks, run the Check CD for Defects choice.  You said you've checked the integrity, but not how.  If you've already done all this, then I have no other suggestions.
How do I check the CD for defects?

---

### Post by bapoumba on 2009-05-08
If you go back to the previous page, I posted a similar experience I had and an old bug report. Looks to me that the cd and the drive are fine by themselves. The problem seems to be a bad detection from the current release if other releases work.

I'll look if I can find a more recent bug report.

---

### Post by sgosnell on 2009-05-08
When the initial screen comes up, the one that asks if you want to try Ubuntu without changes, install, etc, scroll down and select the option to check the CD for defects.

---

### Post by jarrettm on 2009-05-11
I have fixed this problem, in a quirky way.

I installed the 8.10 CD, updated all the fixes and then used the upgrade option. (I could also have tried the advanced CD).

It seems to work.

My conclusion is that...
1.  The CD was fine (it ran on three other machines, including the CD integrity check and the MD5 check on the download).
2. The DVD drive was fine, it loaded 8.10 effortlessly.
3. That there is a quirk where, on some machines, the CD boots, and then forgets whence it was booted when the menu pops up.

---

### Post by jarrettm on 2009-05-11
Well I thought I had fixed it, but the machine cannot see the DVD drive! So it's back to 8.10 for me.

---

### Post by jarrettm on 2009-05-11
I repartitioned the disk and put 8.10 on the machine. This delivered the 2.6..27-7 kernel. On rebooting this kernel gives me my DVD. 2.6.28-11 does not.

---

### Post by sgosnell on 2009-05-11
Did you try [2.6.29 kernel](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb)?  It improves the compatibility of many laptops.  You don't have to reinstall the complete OS to change kernels, just install the .deb for the kernel, and you can have as many kernels installed as you like, and boot from any by pressing Esc at the start of the boot sequence.  I currently have the .28, .29, & .30rc4 installed, and plan to install the .30rc5 tonight.  I'll probably remove the rc4 after insuring the rc5 works.  If I ever have a problem with one of the kernels, I can just boot from another and remove the troublesome one.

---

### Post by jarrettm on 2010-01-24
I'm deeply embarassed.

This turns out to be a hardware configuration issue. The drive was configured for cable select, when it should have been forced to master/slave.

Why it generally booted but did not appear under Ubuntu is still a mystery. I guess thr bios finds any bootable device anywhere on the IDE bus? Once Ubuntu is up, I guess it needs a proper configuration.

My apologies to anyone I have misled.

---

### Post by llawwehttam on 2010-01-24
> **jarrettm said:**
> I have fixed this problem, in a quirky way.

I installed the 8.10 CD, updated all the fixes and then used the upgrade option. (I could also have tried the advanced CD).

It seems to work.

My conclusion is that...
1.  The CD was fine (it ran on three other machines, including the CD integrity check and the MD5 check on the download).
2. The DVD drive was fine, it loaded 8.10 effortlessly.
3. That there is a quirk where, on some machines, the CD boots, and then forgets whence it was booted when the menu pops up.

I have seen NO 3 on fedora live CD's before but only if you run the disk check. When I skipped the check it would work fine. Guess this isn't the problem you've been having but if anyone experiences that problem I have seen it before.

---

