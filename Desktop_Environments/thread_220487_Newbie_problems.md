---
title: "Newbie problems"
date: 2006-07-21
forum: Desktop Environments
---

### Post by hokum on 2006-07-21
My first time with Linux. Impressed so far but I've got stuck in a few places...

1) I used the instructions [given here](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only) and attempted to have one of my NTFS-formatted hard disks available each time I start Ubuntu. Not only can I not see any files (file browser just shows a blank window) but I now can't delete the icon it's placed on my desktop. I'd like to be able to access my files, but otherwise how do I get rid of this?

2) Flash. Looking around it doesn't look as though it works much at all, but it keeps giving me this error when I try to install:

```
 sudo apt-get install flashplugin-nonfree Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree

```

3) I'm trying to install Kxdocker. I thought I did it through Synaptics - it certainly shows up as installed - but it doesn't appear on any menus. How do I activate it?

4) I've got a Creative Sound Blaster X-Fi. Is this supported at all because I've got no sound whatsoever.

5) This is what happens when I try to get Adobe Reader:
```

sudo apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  acroread-debian-files
E: Package acroread has no installation candidate

sudo apt-get install mozilla-acroread
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-acroread

sudo apt-get install acroread-plugins
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package acroread-plugins

```

What's going wrong here?


Sorry for the long post :)

---

### Post by someguyouknow on 2006-07-21
1) trying to do the same so i cant help you there

2) i used Automatix to get flash.  EasyUbuntu will do the job for you too.  Otherwise, i dont think you have the repositories for it enabled

3) try typing kxdocker in run command..... 

4) no clue.....

5) i dont think you have the repositories for it enabled

I am still a noob too.....

---

### Post by avtolle on 2006-07-21
Would you be so kind as to edify us on your system specs? TIA.

---

### Post by hokum on 2006-07-21
Ah, Kxdocker worked, cheers :) 

Erm, so which repositories do I need for all that? I thought I'd got them all.

> Would you be so kind as to edify us on your system specs? TIA.

Sure.

AMD FX-55
Abit AN8 mobo
2GB RAM
Nvidia 7800GTX
Creative X-Fi
74GB WD Raptor primary HDD (Win XP)
250GB Hitachi secondary (NTFS formatted)
120GB Samsung tertiary (Ubuntu)
2x NEC DVD-RW

---

### Post by someguyouknow on 2006-07-21
i dont know the exact one.....
i have the "complete" list of repositories but i have no idea which one it is.....
[http://italy.copybase.ch/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://italy.copybase.ch/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)
glad i can help on at least one of them.....lol

---

### Post by philippe_carlo on 2006-07-21
(1) If you want to mount ntfs partitions at boot-up, you need to add the auto-instruction to the /etc/fstab line as follows:
```

/dev/hda1    /media/windows ntfs  auto,nls=utf8,umask=0222 0    0

```

(2) Flash plugin support for Linux is quite bad, although most flash sites using versions below 8, should work fine. If you want the non-free flash player you need to add the corresponding repository in /etc/apt/sources.list similar to the following:

```
deb http://be.archive.ubuntu.com/ubuntu dapper main restricted  universe multiverse

```

(3) Try pressing Alt+F2 and type kxdocker. You can easily create launchers or add a corresponding entry to the menus using the menu editor. Probably, the kxdocker package does not add it's entry to gnome menus

(4) Sound can be tricky sometimes. Apparently, Creative is working on closed source drivers. In the mean time, open source driver development seems to experience problems. See [http://www.ubuntuforums.org/showthread.php?t=78495]("http://www.ubuntuforums.org/showthread.php?t=78495")
Bummer!

(5) Adobe reader is also in the multiverse repository, I believe. But may I reccomend KPDF? Way better (read: faster).

---

### Post by avtolle on 2006-07-21
Thank you for the specs, hokum. Are you using the 64-bit install? If so, be advised that your Flash problem, at least, is related to this. I think this also may apply to the Acroreader issue, too.

---

