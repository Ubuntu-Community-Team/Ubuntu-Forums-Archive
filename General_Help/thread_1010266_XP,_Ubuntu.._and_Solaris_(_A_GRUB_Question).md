---
title: "XP, Ubuntu.. and Solaris? ( A GRUB Question)"
date: 2008-12-13
forum: General Help
---

### Post by puscifer919 on 2008-12-13
Hello everyone. Long time visitor, first time poster. =P

Got a quick question about Solaris and GRUB.

I've got a new custom PC with XP Pro and Ubuntu 9.04 on it. I'd like to triple boot and give Solaris a shot, but I don't know a whole lot about GRUB.

When I set the system up, I installed XP, then created a new partition for Ubuntu and loaded GRUB as the default bootloader. Now I need to figure out a way so that when I install Solaris on a new partition, I don't overwrite the bootloader with something else, and also find a way to make GRUB see the Solaris install.

I'm a novice-medium level Ubuntu user, and I have no Solaris experience (hence wanting to install it), so let me know what additional information you need.

Thanks in advance! :D

---

### Post by albinootje on 2008-12-13
What is the reason that you want to try Solaris ? 

If the only reason is that you want to play with ZFS, you might as well run it inside VirtualBox with a few virtual hard disks.

I've installed OpenSolaris some time ago, and i was surprised about how much RAM it want for the installation, and after the installation i was not sure why i ever wanted to use it on the desktop.

Apart from that, ZFS looks supercool, but i've used it on FreeBSD for an experimental backup-server setup, and i've read quite a lot from via search-engines and on the FreeBSD fs mailinglists, but my conclusion is that ZFS is still not good enough for recent hardware with a lot of RAM.
Even people with machines with 4 Gb of RAM sometimes had some problems with it.

I've tried also MilaX, an OpenSolaris derivate in VirtualBox, that was pretty nice to try.

---

### Post by puscifer919 on 2008-12-13
> **albinootje said:**
> What is the reason that you want to try Solaris ?
No real great reason other than to try it. It looks nice, I've heard a lot of good things about it, and I've never used it, so why not? Come to think of it, those were the same reasons that led me to installing Ubuntu, which has since become my primary OS on both my PC and MacBook. :D

I do have 4GB of RAM, along with an E7200 (3.20Ghz OC) and plenty of extra hard drive space.

I'd also like to try FreeBSD and a few other Unix distros as well. Losing access to my XP partition is the only real caution of mine as it holds all of my games and such (backed up, but a bitch to reinstall).

Good info [here](http://ubuntuforums.org/showthread.php?t=113743)? (see Post #5)

---

### Post by albinootje on 2008-12-13
Okay :)
I didn't want to discourage you from trying.
From time to time i like to try a lot of software myself.

For that i find VirtualBox pretty cool.
And if you want to try Solaris then there's one advantage by using VirtualBox. Since a while VirtualBox is owned by Sun MicroSystems, and of course they've been working hard to support Solaris better in VirtualBox.

About FreeBSD: I think it's cool, i still use it for some firewalls, and have used it on webservers and mailserver in combination with FreeBSD jails".

Have fun playing around! :)

---

### Post by puscifer919 on 2008-12-13
[QUOTE=albinootje]Okay :)
I didn't want to discourage you from trying.[/quote]
You didn't one bit. :)

[QUOTE=albinootje]For that i find VirtualBox pretty cool.
And if you want to try Solaris then there's one advantage by using VirtualBox. Since a while VirtualBox is owned by Sun MicroSystems, and of course they've been working hard to support Solaris better in VirtualBox.[/quote]
I'll have to give VirtualBox a try, it seems. Thanks!

In the meantime, can you (or anyone) provide some insight to the GRUB issue? If I did decide to install Solaris on it's own partition, what would be the best way to effectively preserve the ability to boot to my other operating systems?

---

### Post by scorp123 on 2008-12-13
> **puscifer919 said:**
> No real great reason other than to try it. Do you have a spare hard drive? That would be best IMHO. Solaris has its own partitioning scheme and mechanisms (e.g. partitions are called "slices" and so on) and it does not take prisoners. If you don't pay attention during the installation your other operating systems will be gone in an instant ... :D

> **puscifer919 said:**
>   It looks nice  Good joke :lolflag:

For "good looks" you'd have to try **OpenSolaris 2008.11** ... it really looks good. But (good old) Solaris 10? Uhmmm, nope :D

> **puscifer919 said:**
>  Losing access to my XP partition is the only real caution of mine as it holds all of my games and such (backed up, but a bitch to reinstall). You should really try Solaris or OpenSolaris in e.g. VMware or VirtualBox first. It's easy to accidentally wipe your harddisk with the Solaris installer ...  The installer of OpenSolaris does a better job and at least suggests to "partition the disk" (btw it looks like a copy-cat of Apple's Mac OS installer IMHO ...) but it's still easy to mess up. Bye bye data, bye bye XP ....

---

### Post by scorp123 on 2008-12-13
> **albinootje said:**
>  ZFS looks supercool You got to be kidding ... "looks supercool". That's the understatement of the year :D

Check out OpenSolaris 2008.11 and its new "Time Slider" feature ...
[http://java.dzone.com/news/killer-feature-opensolaris-200](http://java.dzone.com/news/killer-feature-opensolaris-200)

This screencast briefly shows it in action ....
[http://blogs.sun.com/observatory/entry/screencast_what_s_new_in](http://blogs.sun.com/observatory/entry/screencast_what_s_new_in)

A super duper nice ZFS-frontend like "Time Slider" is a very very good reason for wanting to switch .... I have OpenSolaris 2008.11 on one of my test machines in my lab with a 20 TB storage attached to it.... The possibilities this stuff opens are mind-boggling :D

---

### Post by cmay on 2008-12-13
i use open-solaris 2008.11 as my office and for my internet usage. it is great. but there is one other distribution that is really nice if you want to try solaris. on the download site you find the ditribution belenix which can be installed on a 1 giga byte usb stick and runs of it like a livecd. that has more programs and two desktop enviroments too choose from. kde and xfce. i think it is really nice to use so i often just plug that in and visit ubuntu forums using belenix on a usb stick .   reading the open-solaris install instructions it seems its not so easy to install wiht linux as it could have hoped to be. but good luck to you.

---

### Post by albinootje on 2008-12-13
> **scorp123 said:**
> You got to be kidding ... "looks supercool". That's the understatement of the year :D

Thanks for that link. :)

My opinion is that ZFS is indeed, as SUN (kind of) calls it, writing history in filesystem-history. 
But at the same time my impression is also, after reading a lot of stuff on ZFS-related mailinglists, is that ZFS is also over-hyped.
I've used ZFS with FreeBSD and some features of ZFS are truly amazing, some of the demonstration videos are awesome, but ZFS need a lot of RAM and tweaking, and even then there's the risk to run into trouble.

For usage in Linux there's the problem that ZFS never can be part of the Linux kernel because of the current license that ZFS uses.

There's an alternative for ZFS in development, which is already an add-on in Debian Lenny, called btrfs : 
[http://packages.debian.org/search?keywords=btrfs](http://packages.debian.org/search?keywords=btrfs)
see also : [http://en.wikipedia.org/wiki/Btrfs](http://en.wikipedia.org/wiki/Btrfs)

This is in heavy development and not yet ready for production use, but this is something which can be used in Linux without performance-loss (ZFS via Fuse in Linux is losing performance).

---

### Post by TeXtonyx on 2008-12-13
I'm fairly certain that grub can be installed to the /boot or /root
partition of Solaris, and not overwrite Ubuntu in the MBR.

Sometimes the install to /boot partition is a bit hidden, take for
example Vector Linux, it's a really clear choice presented. But,
for Ubuntu the choice is in Step 7, Advanced, of the live cd install.

Afterwards, do a sudo fdisk -l (small L) and note the partition
that you installed the Solaris boot files to. Then you can add
it to your menu.lst like any other multi-boot OS. Or if Solaris
has a menu.lst, just copy the part that describes title, root etc.
and paste it below Ubuntu. 

Even if you install Solaris to the MBR, it takes about 5 minutes
to reinstall grub, mostly the bootup time of the Ubuntu live cd.

sudo grub
grub>find /boot/grub/stage1
grub>root (hd0,x) where x is the partition reported from "find".
grub>setup (hd0)
grub>quit 

This assumes you have one hard drive. Otherwise, hd1 is possible.

---

### Post by scorp123 on 2008-12-13
> **albinootje said:**
>  I've used ZFS with FreeBSD ... but ZFS need a lot of RAM and tweaking ...  That's surely because of some bugs in FreeBSD. :D  See below.

[http://en.wikipedia.org/wiki/Zfs#BSD](http://en.wikipedia.org/wiki/Zfs#BSD)
> Pawel Jakub Dawidek has ported and committed ZFS to FreeBSD in **_experimental capacity_** for inclusion in FreeBSD 7.0, released on February 28, 2008.[16] The current recommendation is to use it only on amd64 platforms with sufficient memory but there is a newer port (commited to -current) which fixes the memory issue. 


Solaris 10 has been using ZFS for quite a while now. With the new Solaris 10 Update 6 you can now use ZFS on your "/" (root) partitions too. And then there is OpenSolaris which Sun builds into their solutions, e.g. "OpenStorage" which is basically a storage appliance (= OpenSolaris 2008.11 + ZFS + a few web GUI's on top) built around ZFS.

If there were any serious problems with ZFS then there would be an awful lot of corporate heavy-weight customers out there who would scream bloody murder and demand the Sun CEO's head on a silver plate ...  :D

But the contrary is the case. I know lots of Unix shops where ZFS is the very reason they are migrating away from whatever they had before. Bye bye HP-UX. Bye bye Tru64. Bye bye AIX. Hello Solaris! Hello ZFS! For the SUN always shines ... :D

---

