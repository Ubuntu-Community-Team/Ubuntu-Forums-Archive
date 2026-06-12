---
title: "[SOLVED] New to Linux - Help please"
date: 2008-11-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thebbxx on 2008-11-24
I have a Dell Poweredge 2500 which I am trying to install Ubuntu on.  I installed the OS from a CD and it went through the whole thing, then told me to remove the CD and reboot.  Problem is, once it gets to the point where it is trying to boot from the HD, it just seems to freeze.  I have never used Linux before but I would imagine if it were working, it would give a command prompt/ask me to log in?

Please let me know what info you need to help me get this going.

---

### Post by __Ryan__ on 2008-11-24
Basically your going to have to be able to see what is going on at boot time. You can do this by removing the Ubuntu splash screen when the computer boots up.

To  do this reboot your computer and when it reaches the grub menu press 'e' to edit the boot entry.  Go to the first line that begins with 'kernel' and go to the very end of the line. Put a '#' before the 'splash' keyword and then go ahead and boot the system.

You should now see where the boot process is hanging.  

Good Luck

---

### Post by thebbxx on 2008-11-24
I don't see a Ubuntu splash screen or a grub menu.  It just hangs on the bios menu at the point when it should be starting to load up.

> **__Ryan__ said:**
> Basically your going to have to be able to see what is going on at boot time. You can do this by removing the Ubuntu splash screen when the computer boots up.

To  do this reboot your computer and when it reaches the grub menu press 'e' to edit the boot entry.  Go to the first line that begins with 'kernel' and go to the very end of the line. Put a '#' before the 'splash' keyword and then go ahead and boot the system.

You should now see where the boot process is hanging.  

Good Luck

---

### Post by __Ryan__ on 2008-11-24
Do you just see a black screen?  The grub menu may be failing to display correctly for some reason.  By default it waits for 10 seconds here before it continues to boot. You might be able to hit enter when it seems to freeze or wait a minute or so for it to continue.

---

### Post by thebbxx on 2008-11-24
Yes, it stays on the black BIOS screen.  The normal BIOS operations remain displayed on the screen, and the last line is something like "BIOS installation successful".  I even changed it so that it would try to boot from CD after the HD, to see if it was even trying to boot, and it didn't boot the CD, so obviously it's getting stuck trying to boot from the HD.

> **__Ryan__ said:**
> Do you just see a black screen?  The grub menu may be failing to display correctly for some reason.  By default it waits for 10 seconds here before it continues to boot. You might be able to hit enter when it seems to freeze or wait a minute or so for it to continue.

---

### Post by __Ryan__ on 2008-11-24
You weren't trying to flash your bios were you?  That seems like a strange message...

I would say for you to boot from the CD and try another install. For some reason the boot sector might not have been written correctly.

---

### Post by thebbxx on 2008-11-24
Yeah, seems like a strange message to me too.  But it says the same thing before booting from a CD, and that works.  I am trying to install again.  I have also tried the option on the Ubuntu CD that says "boot from the first hard drive."  And that hangs also.

---

### Post by thebbxx on 2008-11-25
I just reinstalled - even used a new CD, and having the same result:confused:

---

### Post by spawn. on 2008-11-25
Ctrl Alt F9 when the screen is black...this happened to me before. But I was running on an IBM/Lenovo ThinkPad.

---

### Post by thebbxx on 2008-11-25
This didn't do anything

> **spawn. said:**
> Ctrl Alt F9 when the screen is black...this happened to me before. But I was running on an IBM/Lenovo ThinkPad.

---

### Post by caljohnsmith on 2008-11-25
I think I might know what your problem is, but how about first booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```

---

### Post by spawn. on 2008-11-25
> **thebbxx said:**
> This didn't do anything

Yeah I didn't think it would either. I thought it would be a good warming up joke.

---

### Post by Dan_Dranath999 on 2008-11-25
[B]That JUST HAPPENED to me 3 days ago!!!
[/B]
I replaced my Hard Disk (it was dying) and installed Ubuntu, But somehow GRUB failed to install, so the system was hanging after BIOS (**[COLOR="Red"]I booted from the LiveCD, and mounted my harddisk: The whole file system from a normal installation was there, so i suspected GRUB was the problem[/COLOR]**) 

I installed Ubuntu Again, but used some "advance options" tab, somewhere in the process, to tell the installation where to put grub... and there you go! Reboot, and everything normal!

---

### Post by sgt_mjc on 2008-11-25
You may have acidentally flashed your BIOS. With that being said, you may need to reflash it with a fresh set of drivers from Dell. I know, what a pain. Hang in there.

---

### Post by thebbxx on 2008-11-25
Disk /dev/sda: 90.9 GB, 90994114560 bytes
255 heads, 63 sectors/track, 11062 cylinders, total 177722880 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cd760

Device Boot    Start    End    Blocks    Id    System
/dev/sda1    *    63    170401454    85200696    83    Linux
/dev/sda2        170401455   177711029    3654787+    5    Extended
/dev/sda5        170401518    177711029    3654756    82    Linux swap / Solaris


> **caljohnsmith said:**
> I think I might know what your problem is, but how about first booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```

---

### Post by thebbxx on 2008-11-25
Hmm..  Yeah, with the live cd, I can see the hard drive and it appears to have the OS files.  There is a folder named boot/grub with 12 files in it, but I'm not sure how to check if it's installed correctly.

> **Dan_Dranath999 said:**
> **That JUST HAPPENED to me 3 days ago!!!**
I replaced my Hard Disk (it was dying) and installed Ubuntu, But somehow GRUB failed to install, so the system was hanging after BIOS (**[COLOR="Red"]I booted from the LiveCD, and mounted my harddisk: The whole file system from a normal installation was there, so i suspected GRUB was the problem[/COLOR]**) 

I installed Ubuntu Again, but used some "advance options" tab, somewhere in the process, to tell the installation where to put grub... and there you go! Reboot, and everything normal!

---

### Post by caljohnsmith on 2008-11-25
Sounds like you might have a problem with how your HDD is configured in BIOS; did you have Windows or any other OS installed on that HDD previously that worked OK? What was on the HDD before you installed Ubuntu?

Just to make sure you have Grub installed properly to the MBR (Master Boot Record), how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Then reboot, and let me know if anything different happens on start up.

---

### Post by upchucky on 2008-11-25
your install is there, it is fine.

grub does not know where the boot sector is.

get advanced supergrub to fix the master boot record.

search the forums for menu.lst it has the info u need to fix the loader. 

grub works in two stages, the first stage tells grub where the bootloader is on the hard drive. the second stage starts when it finds the bootloader and then uses the information in the menu.lst to see what os to load.

---

### Post by thebbxx on 2008-11-25
Hey, thanks for your help - I really appreciate it.  When I try root (hd0, 0) it says Error 11: Unrecognized device string.

I just bought this server from craigslist and nothing was on it, but the guy said that windows was running fine on it before.

> **caljohnsmith said:**
> Sounds like you might have a problem with how your HDD is configured in BIOS; did you have Windows or any other OS installed on that HDD previously that worked OK? What was on the HDD before you installed Ubuntu?

Just to make sure you have Grub installed properly to the MBR (Master Boot Record), how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Then reboot, and let me know if anything different happens on start up.

---

### Post by caljohnsmith on 2008-11-25
It looks like you got that error because you have a space after the comma: (hd0, 0) should be (hd0,0). How about trying again, but if you can, please copy and paste the commands from my previous post so there is less chance of a accidentally having a typo.

---

### Post by thebbxx on 2008-11-25
You are the man!  It works now:guitar:


> **caljohnsmith said:**
> Sounds like you might have a problem with how your HDD is configured in BIOS; did you have Windows or any other OS installed on that HDD previously that worked OK? What was on the HDD before you installed Ubuntu?
Just to make sure you have Grub installed properly to the MBR (Master Boot Record), how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Then reboot, and let me know if anything different happens on start up.

---

### Post by caljohnsmith on 2008-11-25
That's great news it turned out to be a simple problem; cheers and have fun with Ubuntu. :)

---

### Post by thebbxx on 2008-11-25
Thanks.  Actually it's a terminal server... about 10-15 people are going to be using linux for the first time!  kind of exciting for me.

> **caljohnsmith said:**
> That's great news it turned out to be a simple problem; cheers and have fun with Ubuntu. :)

---

