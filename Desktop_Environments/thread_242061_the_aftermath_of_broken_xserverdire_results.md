---
title: "the aftermath of broken xserver:dire results"
date: 2006-08-23
forum: Desktop Environments
---

### Post by keith whitehouse on 2006-08-23
hi all,

I have 2 hard drives, the first with XP on it (10 partitions using "Hyperos"). The second drive is just "Ubuntu"' On the Ubunto Dapper Drake drive I have root, home and swap.


Like a lot of other people I got caught out by the update, and there starts my problems. I tried all of the suggestions, non worked. In desperation I thought that as a last resort I would reformat the root partition and then re-install Dapper, as I have a seperate home partition.

Using my Gparted live cd I found that it would not correctly boot, so thinking that it could be damaged I download the latest version of Gparted. This started to boot but then put a message on the screen "error kernel panic-not syncing-attempted to kill inst"

I tried the Dapper live cd and when prompted with the 2 options I chose install. I elected to manually make changes to the partitions, still hoping to keep my home partition. The orange bat just keeps going from side to side but finally puts up a message after more than an hour, "Installer crashed".

On boot I now get a grub 15 error

I am unable to boot into WindowsXp (presumably becuse Grub does not exist)

Booting from the Windowsxp disc and going into recovery mode, it says that there are NO disc installed on the system, and terminates.

What now, as thanks to an error with the update and no doubt to some errors by me in trying to fix it, I have a WindowsXP Professional disk with 10 partitions of programs and data which is irriplaceable and which I cannot access, and I have a second drive  containing Ubunto Drake that will not boot. I cannot reformat my root linux partition to install Dapper Drake again from scratch

Having worked all night on it and feeling just a bit grumpy I could really do with a bit of help please.

best regards keith

---

### Post by mlind on 2006-08-24
Hi, I'm not sure why people go and reformat their root partitions so often when a problem occurs. I'm not sure what instuctions you used, but with less than a minute I was back in running Xserver.

xserver-xorg-core was the only update released on this week (or in two weeks?), so it must be the problem why everything worked fine before
```

#find the earlier version
apt-cache show xserver-xorg-core | grep Version

sudo aptitude install xserver-xorg-core=1:1.0.2-0ubuntu10
sudo /etc/init.d/?dm restart

```

I suggest you to learn to use powerful apt interfaces like aptitude, apt-get or adept. Only reinstall when everything is lost, because then you'll fail to learn anything.
You should also view any logfiles on /var/log because the often hold the information that will provide useful.

I know that this is bit advanced stuff, and there really should be a rollback or system restore feature. Especially when GUI breaks..

---

### Post by keith whitehouse on 2006-08-24
Hi mlind,

thanks for the reply, and you correctly assume that my knowledge of Linux is indeed very limited. Your suggestion does not apply now as not using my computer to play games, or indeed for personalizing the display, I actually use it to work with. In desperation and not wanting to loose the information contained on the C: drive, (all 10 Hyperos drives) I have had to take the plunge and try to salvage what I can. I have left everything to do with the C: drive alone

I still cannot use the latest Gparted disc to try and reformat the root partition it fails with kernel panic. I have used the Dapper Drake Live CD and let it automatically make the partitions on the Ubuntu drive. It says that ony 2 partitions will be changed which means that it is not able to access the original root partition. I let it install and then checked what partitions I have on the Ubuntu drive. I have a root partition of 73 gig and a swap partition of about 1 and a half gig, but NO sign of the original root partition. I think that the only way that I may be able to get the whole drive back is to boot from a Win 98 boot disk and use Fdisk, but I am tempted to stay as I am and just loose the first 10 gig of the drive, this is just out of relief at being able to have a grub menu and be able to get back into 15 years of data.

If you have the time and patience, is it possible to make a home partition now that I am where I am.

many thanks for your help and I will obviously have to learn a lot more about Ubuntu before I go any further as there was a lot of stuff lost that I doubt very much that I will be able to replace.

best regards keith

---

### Post by enopepsoo on 2006-08-24
if windows won't boot either, it sound like your disk has failed.  maybe this hyperos thing is causing you some problems.

---

### Post by Malac on 2006-08-24
Without wanting to preach(but I'm going to) :grin:, this is yet another reason to keep good backups.
I was back up and running within 1 hour. Only had to restore one partiton.

Backup on a partition by partition basis, CD-R's are so cheap now that one a week is not that expensive especially if it is saving 15 years of work.
Also a FreeDOS boot disk containing FreeDOS FDISK with the MBR's of all the Drives on your system is a must IMHO.

Sorry that this is not very helpful but maybe it will help with future problems.

---

### Post by logout on 2006-08-24
Someone please correct me if I'm wrong here because I have absolutely no idea what hyperos is, and I haven't done this in a while...

But if my grub died and I was unable to reinstall it, I might try reinstalling the windows bootloader by booting with windows rescue disks and typing 
```

fdisk /mbr

```

which would write the windows bootloader over top of grub temporarily, letting you start windows.

Grub consists of more than one part, one part is in the mbr (master boot record) and the other part is probably in your root partition.  It runs the mbr part first, and if it could not read your root partition because it's messed up, it might give you that sort of error.

In fact I'll look up the error for you. [http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml) 
Error 15 means:

```

 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

/grub/stage1 is the second part of the bootloader I was talking about, if it can't find it, it means your root partition is probably hosed from messing around with gpartd somehow.

Maybe try Windows fdisk as I said.

---

