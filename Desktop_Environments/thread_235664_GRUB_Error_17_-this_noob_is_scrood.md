---
title: "GRUB Error 17 -this noob is scrood"
date: 2006-08-13
forum: Desktop Environments
---

### Post by tudsy on 2006-08-13
Thought Sunday would be a nice day to try to give Ubuntu 6.06 a try.  I know can't boot anything.

I started out with the following partitions (all on a single Wester Digital 160GB drive):

dev/hda1 fat32 (containing windows system stuff)
then an extended partition in NTFS (containing data, media,etc.)

I used Gparted in the Ubuntu Install program to free up some (unallocated) space from dev/hda1, then went back and selected the 'use largest free space' option from the installer menu.  Everything was fine, until I tried to boot and got Grub error 17.

Now, booting from the LiveCD I get the following information when running the installer (just to see what's up, didn't do the install)

/dev/hda1 fat32      lba
/dev/hda3  ext3      boot
/dev/hda2  extended  lba
  /dev/hda6 linuxswap
  /dev/hda5 ntfs   (note, there's little exclamation point icon between 'hda5' and 'ntfs)

That's where I'm at, any help would be huge.
Thanks!

---

### Post by tudsy on 2006-08-13
Oh yeah,
My goal is to have a dual boot configuration with XP and Ubuntu (if all goes well, i'm not opposed to ditching XP somewhere down the road, but not yet).

And I looked through the forums, tried the suggestion of running the XP CD and trying the 'fixmbr' command, but that just seemed to make things worse.
Upon bootup I got a 'cannot load operating system' message.  I reinstalled Ubuntu and am back to the Grub error 17.

Thanks y'all.

---

### Post by foolsh on 2006-08-13
off topic what is the fat32 partition for

when want to dual boot a system i go for the clean install option
if dont have anything you need to save i recommend this route its easier

install windows first (for easiness) only using enough space for just that and a few games and apps then install linux using the rest of the space
it should work fine this way
but if you have things to save on your harddrive then its more complicated

---

### Post by tudsy on 2006-08-13
I really don't want to wipe my hard drive clean.  I have back ups of all critical data, but lots of music is on there I don't want to lose.  Also, I have a pretty clean, well functioning XP install and don't want to have to re-install if at all possible.  Though of course I'd rather re-install XP than have to re-format.

---

