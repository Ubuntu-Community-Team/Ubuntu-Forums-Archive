---
title: "Making Room For XP"
date: 2007-09-30
forum: Dell  Ubuntu Support
---

### Post by LinuxOn1420 on 2007-09-30
I have a Dell 1420N that shipped with ubuntu installed (and working very nicely).  I need to add a dual boot of Windows XP.

The easiest way to do that would be to shrink the last partition and install Windows XP there.  Unfortunately, Windows XP is a little brain dead and assumes it can do whatever it wants with the first writeable partition it finds.  Now I can hide the first two partions and Windows XP will install into the last one but it will probably map it as I: or J:.  The problem is that many of programs built for Windows XP are also brain dead and assume that the system drive is the C: drive.

I tried using gparted to hide the Linux partitions but it will only hide the first two leaving the other four visible to Windows XP.

Is there someway to hide all of the Linux partitioins so Windows thinks it is installing into a "C:" drive?

---

### Post by ridgeland on 2007-09-30
With the Dell installation Dell used several small partitions that may also get in the way.
I have a Dell-Ubuntu but have no plans of putting anything MS on it.
A system that new should have plenty of space to copy the partitions to a new location and let MS have what it will take anyway.  I would use 
# cp -a
Also GRUB will be destroyed.  I've reinstalled Linux before to get past a messed up GRUB and get GRUB reinstalled.  There must be an easier way but finding it seemed more trouble than reinstalling.

This is a good point to recommend my strategy for partitioning.
I use several partitions for Linux, several distros and have space for Ubuntu 7.10 while still keeping Ubuntu 7.04 until I'm convinced I won't be losing anything.  I use 7 to 10 GB per OS partition, then a large partition for Data (includes OpenOffice, Music, Images, etc).  I have a second Ubuntu 7.04 just as a sand-box to test any software I read may be useful.
cp -a should let you clone your working Ubuntu partition to a new partition. Then add it to GRUB and verify it's fine.
I think you can have 16 partitions on each hard drive so now is a good time to set them up.  Then install Windows giving up the first partition and GRUB.  Then install Ubuntu to a blank partition and edit GRUB to add back the clone of the original Ubuntu (cp -a) which will have all the things you've set up and are using now.

---

### Post by LinuxOn1420 on 2007-10-01
I understand your comments -- I don't think you understand my requirements.

I have a factory installed ubantu system from Dell.  I want to maintain that system while also being able to dual boot Windows XP.  (I realize the use of XP is irrational but I need it for reasons that cannot stand the light of day.)

I would like to experience the minimum pain in installing and -- dare I say it -- using Windwos XP.  Windows xp is happiest if it is intalled to what it considers to be the C: partition -- the first partition on the 0x80 hard drive.  Not only is Windows XP happiest there but most of the brain dead applications that run under Windows XP expect to also be in C:\Program fFles\...  

Being the kind and mercifull person that I am I would like to let Windows Xp (and its brain dead applications) to think it is installed on the first partitiion on the first disk drive.  Thus the question as to how to hide the real world from Windows XP.

---

### Post by MikeRussell on 2007-10-02
Why not use vmware to run XP virtually?  I have installed and it's essentially like running it natively...  If you are running the Feisty kernel (2.6.16 I believe) you can get it from either Synaptic or add/remove programs.  If you use Gutsy or have another kernel, you can compile it yourself.  A really simple and useful tutorial can be found here:

[http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html](http://igordevlog.blogspot.com/2007/07/vmware-in-ubuntu-gutsy-kernel-2622.html)

Hope that helps!

Mike

---

