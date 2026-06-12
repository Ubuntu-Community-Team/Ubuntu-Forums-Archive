---
title: "how to upgrade to kubuntu 5.10?"
date: 2005-09-13
forum: Desktop Environments
---

### Post by pesachzon on 2005-09-13
how to upgrade to kubuntu 5.10?
thanks

---

### Post by mlomker on 2005-09-13
Edit your /etc/apt/sources.list to point to Breezy instead of Hoary. Then:

Ctrl-F2 over to a text console and login as root.
killall kdm
apt-get update
apt-get dist-upgrade

I don't recommend it.  It has major problems.

---

### Post by Heart on 2005-09-14
You don't recommend it because breezy isn't stable yet or don't recommend to upgrade in general  :confused:

---

### Post by ltmon on 2005-09-14
[QUOTE=Heart]You don't recommend it because breezy isn't stable yet or don't recommend to upgrade in general  :confused:[/QUOTE]

apt-get dist-upgrade works pretty well in general, so I think he must meen that Kubuntu Breezy has some major issues.

I know that I'm going to wait for a little while, given that there's no "killer feature" that Breezy has for me.

L.

---

### Post by treris on 2005-09-14
Yeah I guess I'm gonna wait too, because so much of the 'new' stuff in breezy has already been backported I hardly need to do a complete upgrade from hoary to breezy, besides breezy is not officially out yet and is bound to have number of bugs left in it, which is not something I'm really looking for

---

### Post by mlomker on 2005-09-14
[QUOTE=Heart]You don't recommend it because breezy isn't stable yet or don't recommend to upgrade in general  :confused:[/QUOTE]

They are making major changes to kcontrol and much of it is broken.  I upgraded about a week ago using a clean install (dist-upgrade **did** toast my box btw) and I couldn't even set the time zone.  I'm definitely waiting until full release before I try it again.

---

### Post by Terracotta on 2005-09-14
[QUOTE=Heart]You don't recommend it because breezy isn't stable yet or don't recommend to upgrade in general  :confused:[/QUOTE]

To upgrade in general is a problem in (k) ubuntu, I haven't upgraded once without having to fix at least some thing. Nice distro, and it's my only choice, but that's something they should work on :|.

---

### Post by shakin on 2005-09-14
[QUOTE=Terracotta]To upgrade in general is a problem in (k) ubuntu, I haven't upgraded once without having to fix at least some thing. Nice distro, and it's my only choice, but that's something they should work on :|.[/QUOTE]

Kubuntu was not available for Warty, so there hasn't been a single dist-upgrade for it yet except for Breezy, which is not released. Are all these broken upgrades going to Breezy? If so, then it's not a problem with the distro, it's a problem upgrading to an unfinished distro.

If you're talking about a regular upgrade, then I think you're in the vast minority. I've only had one problem when a KDE package conflicted with another. It still didn't harm my system in any way, it just refused to upgrade that package until I removed the incompatible one from my system.

---

### Post by najames on 2005-09-14
I did a fresh Kubuntu Breezy 5.10 64bit install last night without problems.
AMD64, Chaintech NF4, Nvidia 6600, Seagate IDE 160gig, etc.  

Pros
Easy install, freshone from scratch and paritioned drives, etc
It is very stable so far
Worked instantly to see other networked machines, excellent!!
Nice mods to Konquerer, good enough to replace Firefox perhaps
Nice Blue desktop
Nice integration of Kontact, mail, calendar, etc

Cons
Not many packages yet, 8>(
I may be wrong, but email import seemed to be missing

Question: If you use the search engine below and find an app for your platform, how do you know if another package, like streamtuner/ripper from Debian's backport, will work with Kubuntu Breezy aside from brute force and trying it?  Gnome vs KDE identification? 

[http://www1.apt-get.org/search.php](http://www1.apt-get.org/search.php)

[http://packages.debian.org/unstable/net/streamtuner](http://packages.debian.org/unstable/net/streamtuner)

Looks like an older version for AMD64 in Debian, will it work?

---

### Post by mlomker on 2005-09-14
A well packaged .deb file will fail to install if the dependencies aren't correct.  Using a Debian repository is dangerous business because customized Ubuntu packages can get overwritten.

I'd recommend compiling from source if your download .deb doesn't work.

---

### Post by Takis on 2005-09-14
[QUOTE=najames]Question: If you use the search engine below and find an app for your platform, how do you know if another package, like streamtuner/ripper from Debian's backport, will work with Kubuntu Breezy aside from brute force and trying it?  Gnome vs KDE identification? [/QUOTE]
It may work, it may not work, it may totally ruin your system. Debian is not the same as Ubuntu (similar, but not the same). Avoid using Debian packages on Ubuntu. 

Like mlomker said, you should compile from source.

---

### Post by hshen on 2005-09-14
[QUOTE=mlomker]Edit your /etc/apt/sources.list to point to Breezy instead of Hoary. Then:

Ctrl-F2 over to a text console and login as root.
killall kdm
apt-get update
apt-get dist-upgrade

I don't recommend it.  It has major problems.[/QUOTE]

I have some other questions related to the upgrade. 

Now I have Hoary on my laptop, which I have hacked a quite bit (the installed kernel simply cannot boot, the machine is Toshiba Satellite M40). I hope Breezy will be much nicer to the laptop but not so sure. My questions are

1. if somehow after dist-upgrade, the system is not in a good shape, how can I move back to the state before the upgrade?

2. Can I have Hoary and Breezy coexist on my laptop? If yes, do I need a separate partition for Breezy? Now I have Window XP and Hoary on the same machine.

Thanks!

---

### Post by mlomker on 2005-09-14
> 
1. if somehow after dist-upgrade, the system is not in a good shape, how can I move back to the state before the upgrade?


Restore a backup.  You could tar the entire / directory and save that file off somewhere, or you could use an imaging program, or ...   There isn't any *apt-get ichangedmymind* if that's what you're asking.    :smile: 

> 
2. Can I have Hoary and Breezy coexist on my laptop? If yes, do I need a separate partition for Breezy? Now I have Window XP and Hoary on the same machine.


Yup, separate partitions...it'll just be another grub selection.

---

### Post by najames on 2005-09-15
Just uncommenting the universe in /etc/apt/sources.lsit gave me all the Ubuntu packages needed so far.

The only problem I have encountered was one time where the display went psycho exactly like it did in Hoary/Gnome on a similar setup.  Someone else here said it it caused by flakey Nvidia drivers.  One would think that by now Nvidia stuff would all be rock solid though.  I need another video card, anyone use ATI?  If it works better I am willing to get one.  I can mix and match parts below.

Two of these
Chaintech NF4 Ultra, AMD64 Winny 3000+, Gigabyte 6600, 1 gig Corsair Valueram.

One of these
MSI Neo2 Plat, Winny 3200+, Nvidia FX5200, 1gig Patriot XBL 2-2-2-5.

One of these, to be assembled
Asus A8N-E, Venice 3200+, no vid yet, 1 gig Corsair Valueram

One waiting for Linux, benchmarked with XP
Tyan Dual CPU 246 Opteron, 2gigs Crucial, onboard video 

Two clunkers, one PIII 800, one K6-500.

---

### Post by hshen on 2005-09-15
[QUOTE=mlomker]Restore a backup.  You could tar the entire / directory and save that file off somewhere, or you could use an imaging program, or ...   There isn't any *apt-get ichangedmymind* if that's what you're asking.    :smile: [/QUOTE]

In Windows, I can simply set a Restore point, and rewind to the state as Restore point. Anything like in Linux?

---

### Post by mlomker on 2005-09-16
[QUOTE=hshen]In Windows, I can simply set a Restore point, and rewind to the state as Restore point. Anything like in Linux?[/QUOTE]

No.  I haven't played with that feature very much in Windows XP but I'm pretty sure it just backs up the registry and not all of your files.  It wouldn't work for an operating system upgrade, which is what we're talking about.

I actually run my test environments within a copy of VMWare, which is capable of doing snapshots like that.  VMWare isn't cheap, though, and that sort of usage is more for software developers....in my case network admin.

---

### Post by greyhound4334 on 2005-09-16
I've been running breezy kubuntu (via apt-get dist-upgrade from hoary) for over a week with some minor problems (firefox and amarok have been a little flakey), but everything else (for me, apache2, php5, jedit, konsole, thunderbird, kate, konqueror) have been pretty solid.  

Streamtuner, streamripper and xmms work fine.   I haven't found a single package  that I used (others include limewire, phpbb2, partimage, rsync, crossover office [wine] and several windows apps running under it) that didn't either exist in the repos, download as a binary and run, or build properly and run.

So far it's been no turning back for me, though I did preserve a back up of hoary in case things went south.

It DOES look like there's 50-200 packages upgraded daily, so I remain nervous about something major breaking, but I figure that if it does, at this stage, a fix should get turned around quite quickly.

---

