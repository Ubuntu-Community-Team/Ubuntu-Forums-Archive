---
title: "root privileges in recovery mode"
date: 2006-03-21
forum: Desktop Environments
---

### Post by stevot on 2006-03-21
Hi,

I've messed up when changing hostname of my linux box :( 

steve@ubuntulaptop:~$ cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost       ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
steve@ubuntulaptop:~$ cat /etc/hostname
ubuntulaptop
steve@ubuntulaptop:~$ sudo nano /etc/hostname
sudo: unable to lookup ubuntulaptop via gethostbyname()

So, sudo is broken. I have never set up a root account, so to fix this I need to somehow get root privileges, which people suggest getting via booting into recovery mode. However when I do this I get a prompt for the root password, which I have never set up (Breezy badger 5.10). I therefore can't get in as root, and can't make the change to /etc/hostname that I think is needed.

I've tried recovery modes for both the original kernal I installed (2.6.12-10-386) and an upgraded one (2.6.12-10-386), no joy

So my question is, how can I get root access when I've always used sudo, that is broken, have never set up a root account, and recovery mode doesn't give it by default. Is there a command line option I can give at the grub login?

Failing that can I use the instal CD to get in (haven't tried yet since I don't want to reinstall) ?

Thanks for any help,

Steve

---

### Post by trent dillman on 2006-03-21
how about mounting the drive read/write with knoppix?

---

### Post by stevot on 2006-03-21
That's an idea - should I be able to mount local drives after booting from the Kubuntu live CD ? (already have that so would save downloading Knoppix)

Steve

---

### Post by stevot on 2006-03-21
... no, don't think the live CD will do it, unless I'm misunderstanding  (a dual boot system, can't recall the exact name of the partition, but I don't see anything with fdisk -l /dev/hda)

---

### Post by jrib on 2006-03-21
you should be able to use the livecd.  Boot into normal ubuntu and type 'mount'.  Then see what partition corresponds to /.  Reboot with the livecd and mount the partition.  Edit /path/to/mounted/drive/etc/hosts.  To fix the problem you are having with recovery mode asking you for a password, edit /etc/shadow and change the password field for root to: *

---

### Post by stevot on 2006-03-21
fantastic - sorted:D 

thanks for your help,

Steve

---

