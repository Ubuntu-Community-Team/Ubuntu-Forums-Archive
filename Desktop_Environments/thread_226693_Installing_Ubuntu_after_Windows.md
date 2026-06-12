---
title: "Installing Ubuntu after Windows"
date: 2006-07-31
forum: Desktop Environments
---

### Post by roflcopter_1 on 2006-07-31
I hate to say it, but I have to reinstall windows. I definitely don't want to lose all the settings/programs/files I have in ubuntu right now, so how should I go about reinstalling Windows? I'm gonna make a second partition for Windows, but beyond that, what should I do? Doesn't Windows overwrite the Grub boot loader? Thanks.

Thread title should say: Installing Windows after Ubuntu.

---

### Post by x64Jimbo on 2006-07-31
After you install Windows, just run this from your Ubuntu install LiveCD:
sudo grub-install <hard disk device... probably /dev/hda>

---

### Post by roflcopter_1 on 2006-07-31
How exactly do I go to a command line off of the live cd?

---

### Post by Paerez on 2006-07-31
to get a command prompt its:
Programs->Accessories->Terminal

---

### Post by roflcopter_1 on 2006-07-31
Oh. I thought there was some way to do it without booting into a live session or whatever. Please don't believe I didn't know how to open the terminal lol. It just takes like 5 or 10 mins for the live session to start. Thanks for your help. And my apologies for the use of Windows and Ubuntu in the same sentence/title.

---

### Post by x64Jimbo on 2006-07-31
You may be able to get a runlevel 2 (text only) environment in a LiveCD. I know Knoppix has this option but I'm not sure about Ubuntu. When you boot the CD, and it gets to the menu, hit F2 and F3 to check out the boot options. If runlevel 2 is in there, that will do the trick for you.

---

### Post by Paerez on 2006-07-31
Yeah a straight command line would be nice, I am not sure if it offers one. Maybe thats what "Graphics Safe Mode" is or whatever.

And you shouldn't be worried about mentioning ubuntu and windows together. It would be unhealthy to deny the existence of competition. Everyone has their own reasons for their choice of operating system. I still run windows in VMWare for when I need it.

---

### Post by jonvel on 2006-08-08
After already having run the Windows XP re-installation (yay viruses and uninformed users!).  Alas, I realized to my dismay that I seem to have lost the ability to bood directly into Linux (short of using the LiveCD).

So, I boot up (in "reduced graphics mode" since I can't remember the boot command to tell it to load in runlevel 2...) start a terminal and:

Drat..  I get an error running

ubuntu@ubuntu:~$ sudo grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

My /dev/hda is partitioned into:
/dev/hda1 - NTFS (40 gig)
/dev/hda2 - Extended 3 (15 gig, that's where my Linux partition normally lives)
Swap Partition

I can see my old linux partition fine (I mounted it under /media/oldlinux for reference), and under /media/oldlinux/boot I see all of the wonderfull stuff that used to be there, it just doesn't like to show up anymore...

More goodies:
df -k /media/oldlinux/boot
Filesystem  1K-blocks Used    Available  Use% Mounted on
/dev/hda2    15852192 5035160  10011776   34% /media/oldlinux

df -k /boot
Filesystem 1K-blocks Used   Available Use% Mounted on
unionfs      1024928 686448    338480  67% /

I dunno, anything else that's useful?

df -kl doesn't list /boot as a separate device, so the instructions on [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub) don't seem to apply (aka, I can't mount /boot in the installation section, so I never get it "back").

If this post is mis-placed, please let me know.

Thanks!

---

### Post by Paerez on 2006-08-08
open a terminal and type:
```
sudo grub
```
then you get the grub prompt, and type:
```
root (hd0,1)
setup (hd0)
quit
```
then reboot.

---

### Post by jonvel on 2006-08-08
Genius.  Silly me!  Thanks for the tip, Mr. Raccoon-like-thing!

Works like a charm.  That'll have to go into my file of useful things...

I probably should have dug a bit more in the man pages...

---

### Post by Paerez on 2006-08-08
I actually got that tip from the Gentoo Handbook, which used to have an incredibly complicated and in-depth all-terminal install. I did it a bunch of times so I remember it. grub-install doesn't work that often.

---

