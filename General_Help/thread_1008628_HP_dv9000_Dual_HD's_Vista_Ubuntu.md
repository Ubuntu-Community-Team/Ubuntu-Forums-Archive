---
title: "HP dv9000 Dual HD's Vista Ubuntu"
date: 2008-12-11
forum: General Help
---

### Post by seanmjohnston on 2008-12-11
I'm totally new to Linux/Ubuntu.  I saw someone running it on a dell in class and immediately was impressed.  A couple months ago I tried installing Ubuntu and ended up having to send my laptop to HP to get factory restored.  Here is my setup.

Custom HP dv9000
Two 120GB HD's
2 GB RAM
Windows Vista Ultimate 64

One of the HD's I don't use at all, nothing is on it.  I want to dual boot Ubuntu by installing it on this empty hard drive but have the ability to share files between Vista and Ubuntu.  Where I ran into problems when I installed it was with GRUB.  Ubuntu worked fine but when I tried to test out vista again all it would do is boot into the recovery partition of the Vista HD.

Can anyone please help me dual boot correctly?  I'm by no means an expert but I am definitely not a beginner.  Please help!  Thank you!

---

### Post by nzadLithium on 2008-12-11
where did you install the boot loader to? It would probably be best if it was on your ubuntu hard disk, then you set your bios to boot that hard disk (That way you wouldn't touch vista at all :D). Ubuntu should have recognised vista during the install, and you should have a boot option for vista in grub.

What exactly is happening when you boot vista normally?

---

### Post by seanmjohnston on 2008-12-11
> **nzadLithium said:**
> where did you install the boot loader to? It would probably be best if it was on your ubuntu hard disk, then you set your bios to boot that hard disk (That way you wouldn't touch vista at all :D). Ubuntu should have recognised vista during the install, and you should have a boot option for vista in grub.

What exactly is happening when you boot vista normally?

I installed Ubuntu from a CD I burned.  After I installed ubuntu to the empty hard drive I would boot up my laptop and GRUB would show up as I expected.  Ubuntu would work just fine but when I would select vista it would boot up only into the recovery partition of the HD that had vista on it.  (HP laptops come with a partition on the OS HD that is for recovery)

---

### Post by seanmjohnston on 2008-12-11
> **nzadLithium said:**
> where did you install the boot loader to? It would probably be best if it was on your ubuntu hard disk, then you set your bios to boot that hard disk (That way you wouldn't touch vista at all :D). Ubuntu should have recognised vista during the install, and you should have a boot option for vista in grub.

What exactly is happening when you boot vista normally?

I think I kinda understand what your saying...so I should boot into the empty hard drive only and use my CD from there?  Can you explain how I would go about doing that?  Do I need to do anything to the empty hard drive first using Vista?

---

### Post by nzadLithium on 2008-12-11
Hmm, i'm thinking its possible that grub might be pointing to the wrong place? And thus starting your recovery partition instead of the windows bootloader?

boot ubuntu put this in a terminal
cat /boot/grub/menu.lst

copy and paste the output here. Hopefully we can get vista to start, as I take it you probably don't want to reinstall vista :p

---

### Post by seanmjohnston on 2008-12-11
> **nzadLithium said:**
> Hmm, i'm thinking its possible that grub might be pointing to the wrong place? And thus starting your recovery partition instead of the windows bootloader?

boot ubuntu put this in a terminal
cat /boot/grub/menu.lst

copy and paste the output here. Hopefully we can get vista to start, as I take it you probably don't want to reinstall vista :p

Vista has already been factory restored.  I have a clean slate and I want to get ubuntu installed correctly the first time so I don't have to send my laptop into HP again.

---

### Post by nzadLithium on 2008-12-11
ah ok then

do you still have the ubuntu partition on the second disk? To find out stick in the livecd boot it in livecd mode.
start a terminal 
type fdisk -l

it should show both of your hard disks, one should be ntfs (probably with your recovery partition as well), while the other will most probably be ext3.

If you can still see an ext3 partition I think its safe to assume ubuntu is still on there :D

---

### Post by seanmjohnston on 2008-12-11
Both drives were wiped with killdisk and then factory restored so the ubuntu partition will not be there.

I was looking at this thread just now:
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

Can you explain to me what the following part means exactly?

NOTE: drives are 'sd??' because these laptops use SATA hard drives.
Recommended for Dual-booting on a laptop with 2 hard drives:

GRUB installed to MBR of sda1
sda1 - Windows
sdb1 - Ubuntu
sdb2 - Swap (Size of RAM, must not be less or hibernate will not work)

This is just what I would recommend for installation. If you have burned off the Recovery CD/DVD's feel free to delete the Quickplay and Recovery partitions. I never used either of them, so they were just wasted space for me. It is best to remove these partitions before installing Ubuntu, but you can remove their GRUB entries later by editing /boot/grub/menu.lst. This configuration also will allow you to reinstall Windows using the Recovery CD/DVD's with losing your Ubuntu installation. These CD/DVD's format your entire first hard drive which would wipe your Ubuntu install. There is no easy way to use the Windows bootloader to launch Ubuntu from different harddrive. I looked into this in case I wanted to remove Ubuntu later. It is probably possible, but it would be very complicated. Installing GRUB to the MBR of sda is your best and safest option.

---

### Post by nzadLithium on 2008-12-11
Just stick the ubuntu disk in now, you shouldn't need to do anything with vista since you have two hard drives, just tell it to install using an entire hard disk. (Make sure you don't pick the one with vista on it).

---

### Post by seanmjohnston on 2008-12-11
> **nzadLithium said:**
> [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

Use that link to install, its probably more helpful :D
That previous post you were looking at was made for an older version of ubuntu which I don't think is supported anymore. Also the link I provided takes all the technical info out that you don't need to know :D

I looked at that link before but it doesn't explain how to do it with two HD's, just one.  That is where I am shaky on.

---

### Post by nzadLithium on 2008-12-11
yeah, thats why i changed my post. Coz i realised u didn't need to do half of that stuff. You just stick the ubuntu disk in, and tell it to install using an entire hard disk. Just make sure you don't pick the one with vista on it :p Oh and just incase, go into your bios, and change it so that it boots from the other hard disk (not the vista one) then hopefully it wont try to mess with vista's bootloader :p

---

### Post by seanmjohnston on 2008-12-11
> **nzadLithium said:**
> Just stick the ubuntu disk in now, you shouldn't need to do anything with vista since you have two hard drives, just tell it to install using an entire hard disk. (Make sure you don't pick the one with vista on it).

That is exactly what I did before and it would only boot up into the recovery partition.  I guess tomorrow I will just take the leap of faith (After backing up) and install it again.

---

### Post by nzadLithium on 2008-12-11
yep. But make sure its set to boot from the one your installing ubuntu to, i'm hoping that will influence the installer to install the boot loader there, instead of playing with the windows disk :D

---

### Post by seanmjohnston on 2008-12-11
> **nzadLithium said:**
> yep. But make sure its set to boot from the one your installing ubuntu to, i'm hoping that will influence the installer to install the boot loader there, instead of playing with the windows disk :D

How would I go about doing that?

---

### Post by caljohnsmith on 2008-12-11
You shouldn't need to reinstall Ubuntu in order to get Vista booting OK from Grub. Can you still boot into Ubuntu OK? If so, please do that, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
sudo xxd -l 2 -p /dev/sda
sudo xxd -s 1049 -l 2 -p /dev/sda
sudo xxd -s 128 -l 2 -p /dev/sda1
cat /boot/grub/menu.lst
```
Note that "-l" is a lowercase L, not a one. We can work from there if you want.

---

### Post by Simian Man on 2008-12-11
I have exactly the same laptop and also failed to setup a dual boot.  I specifically got one with two HDDS because I thought it would make a dual-boot easier, but it didn't.  I eventually got the dual boot to work by installing both Ubuntu and Vista on the first Hard drive and just using the second one for shared data.  It was much easier IMHO.

When Intrepid came out, however, I wiped Vista out :)

---

### Post by nzadLithium on 2008-12-11
caljohnsmith he wiped the disk, thats why he needs to reinstall.

---

### Post by nzadLithium on 2008-12-12
> How would I go about doing that?

When your starting up, at the first screen that shows, you'd have to hit delete or f2 not sure which. Then in the stuff that shows up you have to find the stuff about boot order/boot devices. DONT TOUCH ANYTHING ELSE or you might find your pc doesn't work XD (easy enough to fix, but still don't touch anything).

Change the boot order so it boots from the other hard disk :)

---

