---
title: "New Ubu User Wants To Know More"
date: 2008-04-26
forum: Desktop Environments
---

### Post by Armaron on 2008-04-26
I'm a fairly new linux user (have been using it for a month or so at work) and I wanted to know more before I started using it at home.

I humbly appologyse if next questions sound from windows, but I've never used anything else than 95 and XP.

First, how does linux handle services? Do they run at startup or do I need to initialise them myself? How would I start or stop these services and is there a place where I can get an overview of what I have installed and what not? (Besides synaptic package manager.) 

Secondly, how does it handle programs? Where does it install them and how? I've installed some programs and seen that they are "scattered about" all over /etc in /bin /lib and other directories.

On Ext3: how does it store files? Does it need to get fragmented after a while? And what about partitions, how does linux handle em and how do I tell them appart.

On connectable devices: how does it handle them? I've seen that they get mounted under /dev and under /media.

If you refer to articles or manuals to read, I don't mind. I want to know a lot how linux handles this. I'm an it student, so I don't mind reading a bit and I would appreciate it if I could get a push in the right direction. Going to look stuff up myself, but I thought it be conveniant to ask you linux / ubuntu guru's about it, so I can get started a lot faster.

Already thanks for any help you're going to give me. :)

---

### Post by bmac on 2008-04-26
I would suggest you start here. Quite a bit of data and multiple links that might help enlighten you....
[http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution]("http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution"))

Hope this helps

---

### Post by Zimmer on 2008-04-26
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

Good place for plain english explanations... The guide to permissions and the directory structure here are  very good examples.
Oh and Ubuntucat's pages and Hermanzone are good for partitioning and installation info.
[http://www.psychocats.net/essays/linuxguide.php](http://www.psychocats.net/essays/linuxguide.php)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by p_quarles on 2008-04-26
> **Armaron said:**
> First, how does linux handle services? Do they run at startup or do I need to initialise them myself? How would I start or stop these services and is there a place where I can get an overview of what I have installed and what not? (Besides synaptic package manager.) 
Most services are initialized during the boot process. Different "runlevels" initialize different services. For purposes of desktop usage, runlevel 2 is the default setup. You can see what starts automatically by looking in the /etc/rc2.d/ directory. 

To start, stop, or restart a service, you would run the associated script in /etc/init.d/ -- this works like so (with the example being cupsys, the printer driver:
```
sudo /etc/init.d/cupsys stop
```
The last word in that command can be replaced with "start", "restart", "force-reload" and a couple others. The all mean pretty much what they sound like. 

> Secondly, how does it handle programs? Where does it install them and how? I've installed some programs and seen that they are "scattered about" all over /etc in /bin /lib and other directories.
The vast majority of executables will be found in /usr/bin. This is the standard path for optionally-installed programs (with "optional" meaning anything that isn't necessary for bare-minimum functionality). The system's core utilities are in /bin. Many executables packaged by third parties, or compiled from source, will be placed in /usr/local/bin, and most games and entertainment packages go to /usr/games. 

Many executables -- just to complicate matters -- are actually scripts that perform simple functions, or call on binaries to do more complicated things.These are stored in /sbin, /usr/sbin, and /usr/local/sbin. 

The files that you see in /etc are not the programs themselves. Mostly, these are configuration settings. As mentioned, though, service start/stop scripts are located in /etc/init.d

It might sound complicated, but it's very straightforward once you get used to it. To locate any executable, simply use the "which" command:
```
which firefox
```
will tell you that Firefox is in /usr/bin.

> On Ext3: how does it store files? Does it need to get fragmented after a while? And what about partitions, how does linux handle em and how do I tell them appart.
Ext3 fragments very slowly. Under typical use, you will never need to worry about it. You can view the names of your mounted partitions by typing:
```
sudo fdisk -l
```
If you have a basic, single-boot installation, your main partition will be called something like /dev/sda1. sda1 translates into "sata disk 'a' partition 1". 

> On connectable devices: how does it handle them? I've seen that they get mounted under /dev and under /media.
Those are two different kinds of files. The file in /dev is the device file, which tells the kernel how to handle the device. The file in /media (or /mnt) is the mount point, which tells the filesystem how to access files on the device.

---

### Post by Armaron on 2008-04-27
Thanks for the usefull reply's. This'll provide me with some good reading for the next couple of weeks. :)

---

