---
title: "Boot Up Troubles"
date: 2006-01-14
forum: General Help
---

### Post by johnnymo87 on 2006-01-14
**Note:** This has been sitting in the beginner forums for a few days unanswered, so I'm moving over here. Daschl said it sounds like my "root partition is mounted with the read only option," and that I should post my /etc/fstab as well, so I posted it at the bottom.

-------------------------------------------------------------------------------------------------------------------------------------

Whenever I boot up my computer and ubuntu begins to load, I run into a strange problem with certain steps failing. It's sorta like my computer skids out on ice, gets stuck in a snow bank, and spins its tires uselessly. Here's how it starts:

[i]
...
Calculating module dependencies [failed]
...
Setting up networking [failed]
...
Synchronizing clock to ntp.ubuntulinux.org [failed]
Initializing random number generator [failed]
...
[/i]

Then the boot up switches to a text version of what was going on (like in recovery mode), focusing in on the 'calculating module dependencies' part. It says:

[i]
...
*Calculating module dependencies...
FATAL: Could not open /lib/modules/2.6.12-9-386/modules.dep.temp for writing: Read-only file system
...
Setting up networking...
/etc/rcs.d/s39ifupdown: line77: /etc/network/run/ifstate: Read-only file system
*Failure initializing /etc/network/run/ifstate
...
*Configuring network interfaces...
/etc/rcs.d/s41hotplug-net: line 12: /etc/hotplug/.run/net.enable: Read-only file
[/i]

Then after waiting for a few minutes, the text on the screen starts repeating this message over and over:

[i]
open: Read-only file system
/usr/sbin/termwrap: line 140: $tmpfile: ambiguous redirect
/usr/sbin/base-config: line 31 /var/log/base-config.timings: Read only file system
[/i]

It keeps on doing this for about 20 seconds until it stops and says:

[i]
* Id "1" respwaning to fast: disabled for 5 minutes
[/i]

Then after 5 minutes, it tries repeating the message again, to no effect. I'm sure if I let it, it would continue like this forever.

The funny this is that this only occurs every other I boot up. Here's what I mean: I turn on my computer at the start of my day, and I run into these errors, which I have grown accustomed to. So then I put my coffee mug down, and reach down and press the restart button on my computer tower.

All of the suddenly my boot up goes smoothly. Next day, same problem.

How can I fix this? It's talking about a Read-only file, but I'm a newb and don't know how to deal with that.

-------------------------------------------------------------------------------------------------------------------------------------

Here's my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by vruum on 2006-01-14
try editing this line 
> /dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
to say
> /dev/hda1       /               ext3    defaults  0       1
I'm not sure it'll work, but it might produce more informative output

---

### Post by johnnymo87 on 2006-01-14
Hm... Did that. No change.

Except that this time instead of entering that loop, it just crashed the X server (Could not start X server due to some internal error). But that may be because I added KDE as the window manager and was messing around with it.

One interesting thing I found while logging in with the recovery mode (because the X server was down) was that right above my command line (is that what it's called in linux?) was this:
*-bash: no job control in this shell*
I don't know if that's normal.

Another thing is that I couldn't log into root (using *sudo -i*). When I tried, it said:
*sudo: Can't open /var/run/sudo/jcm05003/tty1: Read-only file system*

So I just hit the restart button on my tower, and, as usual, everything loaded fine.

---

### Post by vruum on 2006-01-14
strange, I'm not at all sure what could be causing this, but I'm still curious. Did this problem occur suddenly, or has it been like this since you installed? do you have any other operating systems on the machine, windows, any other linuces? if so, do they work? your partitioning scheme seems a little funky, /dev/hda5 would, I think, imply an extended partition, how did you partition the drive? what is the output of 
```
 sudo fdisk -l 
```?
do you have a live cd of any kind that you could use to boot up the machine? 
and, what happens if, once you get the computer running, shut it down, (not rebooting) and then turn it back on? what happens if you just reboot it?
Ok. sorry about all the questions. Just trying to firgure out where the problem resides.

---

### Post by johnnymo87 on 2006-01-14
> Did this problem occur suddenly, or has it been like this since you installed? 
I have install ubuntu breezy 5.10 over tens times over the past few weeks. Same problem each time.

> do you have any other operating systems on the machine, windows, any other linuces? if so, do they work?
Nothing but ubuntu breezy 5.10 

> your partitioning scheme seems a little funky, /dev/hda5 would, I think, imply an extended partition, how did you partition the drive?
If I remember correctly, I had 7GB for /, 10.4GB for /home, and 3 GB for swap. Messed up, I know, but I've also done it with less than 1GB in swap and the rest in /, and nothing else. Same boot up problem.

> what is the output of ```
 sudo fdisk -l 
```?
[i]Disk /dev/hda: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2140    17189518+  83  Linux
/dev/hda2            2141        2501     2899732+   5  Extended
/dev/hda5            2141        2501     2899701   82  Linux swap / Solaris[/i]

> do you have a live cd of any kind that you could use to boot up the machine?
Yes, I have a live CD. 

> and, what happens if, once you get the computer running, shut it down, (not rebooting) and then turn it back on?
50% of the time I can make it through the boot up, 50% of the time I have to restart.

> what happens if you just reboot it?
50% of the time I can make it through the boot up, 50% of the time I have to restart.

I'm not kidding. It really goes 1 for 1 in success and falure.

---

### Post by Mustard on 2006-01-14
One thing I think is worth mentioning with regard to this problem is that your fstab is normally setup to mount the drive as read only should the system find errors on the hard drive.  I would suspect that this is the issue.  The system is encountering a problem with the hard drive, it then proceeds to remount it as read only, which then leads to the system not being functional, as certain files that need to be written to are now read only.

I would be diagnosing your hard drive for possible problems with the hardware.

Now to check your hard drive you would need to run fsck on it, but you can't run fsck on a mounted drive, so you would need a liveCD to boot up, then you would run fsck on the drive in question.

I would read over the manual for fsck too..type this in terminal to see the manual..

```
man fsck
```

Hit 'q' to exit the manual. (Just in case you didn't know) :)

---

### Post by johnnymo87 on 2006-01-14
alright, I'll check it out. My hard drive is about 8 years old.

---

### Post by vruum on 2006-01-14
well, assuming that your live cd can mount the partitions correctly every time. they're probably not the problem. I'd suggest, just for the fun of it, messing about with the access methods of your harddrive in the bios, it's probably set to auto, try setting it to LBA or whatever other options are there, if nothing makes any difference, then maybe try another linux. it might just be that Ubuntu for some reason has a problem with the drive or some other part of your hardware.

#edit: I'm slow, mustard might be on to something, but. fsck, as far as I understand checks the filesystem, not the drive? But then again, an 8 year old harddrive might be kind of flaky.

---

### Post by johnnymo87 on 2006-01-14
I'm a newb, so I don't know all the terminal commands.

I booted up with the live disc, opened the terminal, and typed "fsck". All it did was give me the version number. What's the command? I skimmed the manual twice, but couldn't find that detail.

---

### Post by Mustard on 2006-01-14
I would think you need to specify the device..for example..

```
fsck /dev/hda1
```

I'm just reading through the manual myself, as I rarely use fsck. :)
What the device is called would depend on your setup. This command below should tell you the names of the partitions on your drive..

```
fdisk -l
```

Having not used a liveCD much, I wasn't sure whether to include 'sudo' in front of that command either, but I would suspect its necessary.

---

### Post by Mustard on 2006-01-14
[QUOTE=vruum]#edit: I'm slow, mustard might be on to something, but. fsck, as far as I understand checks the filesystem, not the drive? But then again, an 8 year old harddrive might be kind of flaky.[/QUOTE]

Yeah, this is true.  Its just one way of diagnosing whether the file system is corrupted due to a flaky hard drive.  From the sounds of the problem though, I am pretty sure the hard drive is dying.

---

### Post by johnnymo87 on 2006-01-15
[QUOTE=Mustard]Yeah, this is true.  Its just one way of diagnosing whether the file system is corrupted due to a flaky hard drive.  **From the sounds of the problem though, I am pretty sure the hard drive is dying.**[/QUOTE]
I would not be surprised if it's true.

Ok, so I ran *sudo fdisk -l* and then *sudo fsck /dev/hda[1,2,5]*. Somewhat interesting results. See if it helps you guys:
[i]
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2140    17189518+  83  Linux
/dev/hda2            2141        2501     2899732+   5  Extended
/dev/hda5            2141        2501     2899701   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo fsck /dev/hda1
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/: clean, 110673/2150016 files, 855684/4297379 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/hda2
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/hda2
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo fsck /dev/hda5
fsck 1.38 (30-Jun-2005)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/hda5
[/i]

As I said before, I think right now my hard drive is partitioned 7GB in /, 10.6GB in /home, and 3GB in swap. 

On a side note, out of the 10+ times I've installed, the installation only has went completely through once. All the other times it would hang up during the package installation for unspecific reasons (error message listed HD space as a factor, which it couldn't be). 

It very well may be time for a new HD.

---

