---
title: "Is it safe to fsck the / partition from single user mode/recovery mode?"
date: 2009-01-14
forum: General Help
---

### Post by jerome1232 on 2009-01-14
My little teamspeak server stop functioning last night after a reboot (ssh wouldn't work, nmap was showing all my ports as closed, it would respond to pings though)

I finally dragged a monitor and keyboard over to it and found that fsck was failing during the root partition check and dropping me to a maintenance shell.

Bear in mind this machine has no cd-roms in it. The root partition is ext3.

Is it safe to run fsck on / from the maintenance shell? Do I have remount / as read only and run fsck on it? Is it safe to even run fsck on a read only partition?

If not then can I boot into recovery or single user mode and run fsck from there?

---

### Post by azzamite on 2009-01-14
Don't know, fdisk says it's not recommended.

Get a live USB pen drive with any distro and boot from it,
those thing are far more useful than a live CD.

---

### Post by jerome1232 on 2009-01-14
Actually it may be the situation is a bit different than I thought. I checked the logs fsck leaves and this is what I get:

I'm not sure why I thought it was the root partition, I could've sworn that's what the original error message was.

```
tss@teamspeak:~$ cat /var/log/fsck/checkroot
Log of fsck -C -a -t ext3 /dev/mapper/teamspeak-root 
Wed Jan 14 10:32:20 2009

fsck 1.40.8 (13-Mar-2008)
/dev/mapper/teamspeak-root: clean, 22048/294912 files, 379229/1179648 blocks

Wed Jan 14 10:32:20 2009
----------------
tss@teamspeak:~$ cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a 
Wed Jan 14 10:32:22 2009

fsck 1.40.8 (13-Mar-2008)
boot: clean, 38/36144 files, 48221/144552 blocks
[COLOR="Red"]fsck.ext3: Unable to resolve 'UUID="570bfc7f-b5d6-4b28-a5db-c6afae1c37b3"'
fsck died with exit status 8[/COLOR]

```

Upon further investigation that uuid was a removable drive that I used to have plugged in, it was supposed to be a permanent drive and so was included in the boot up fsck sequence. fsck panic'd when it couldn't find the drive. For now I'll comment it out of fstab but is there a way to get fsck to gracefully handle that, I want the drive to be fscked every now and then but need that server to boot if the drive is removed.

@azzamite do you know of any live distro's that would fit on a 512mb stick, all I would need is a core command-line system with the basic utilities, including lvm2 management.

---

### Post by azzamite on 2009-01-14
> **jerome1232 said:**
> 
@azzamite do you know of any live distro's that would fit on a 512mb stick, all I would need is a core command-line system with the basic utilities, including lvm2 management.


I installed Debian Lenny the hard way (using debootstrap)
Base systen (command line) about 200M
[http://www.debian.org/releases/stable/i386/apds03.html.en](http://www.debian.org/releases/stable/i386/apds03.html.en)

But mabe this could be usefull
[http://www.pendrivelinux.com/all-in-one-usb-dsl/](http://www.pendrivelinux.com/all-in-one-usb-dsl/)

I think you can use UNetbootin to put a (live) ISO in your
pendrive but I'm not shure.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

