---
title: "Nautilus Places vanish &amp; configuration reverted to default"
date: 2009-10-20
forum: Desktop Environments
---

### Post by inspired on 2009-10-20
Hi folks,
My home folder became full (unexpectedly) when I tried to rip a CD to mp3 files.
I didn't know this had happened.. just noted that the rip failed. I was in a hurry, shut down my computer, and the next time I started it a few things would not load.. in particular AutoKey was saying the device is full.
I figured out the HOME space was full.

It also affected Nautilus, and the issue did not resolve once I made more space in /HOME

The custom and system default Places do not appear, and the config reverted to some default configuration. For instance, I use to see all folders in List view by default but it has now reverted to the Icons view by default.

Is there a backup of Nautilus settings I can restore? Meaning, does N. keep a backup?

Is there any easy way to restore all the folder shortcuts I had in Places or do I have to recreated them all (not that I remember them all by heart).

With much thanks for any help you can provide...

Jonathan

PS. In the Places view in N. I see everything above the horizontal line:
```
Jonathan
Desktop
File System
Network
[my winxp partition mount]
Trash
```
Then there is the horizontal line. There is nothing under that. I use to have a list of all the default older shortcuts, plus my custom ones.

---

### Post by earthpigg on 2009-10-20
hi,

let's verify that your /home is indeed full if we could?

please post output of this, in [ CODE ] tags (no spaces before/after [, though):

```
df -Th
```

and, do you have a full backup of your /home? (if you don't, in the future i suggest making one :D )

if so, we can selectively restore nautilus' settings.

---

### Post by inspired on 2009-10-20
> **earthpigg said:**
> hi,

let's verify that your /home is indeed full if we could?

please post output of this, in [ CODE ] tags (no spaces before/after [, though):

```
df -Th
```

and, do you have a full backup of your /home? (if you don't, in the future i suggest making one :D )

if so, we can selectively restore nautilus' settings.

Thanks...
Home had only 148k free space when I rebooted and caused this issue to arise. I have since delted some stuff and it now has 208MB. I intend to move a lot more stuff to an external HDD, but I figured 208mb free space would be fine in terms of apps accessing and using their files.

Jonathan

---

### Post by earthpigg on 2009-10-20
what did df tell you, exactly?

Linux filesystems generally need to be ***less*** than 95% used to really work properly. i personally start to make myself become concerned and start planning for the future if i get over 85%.

this is the price we pay for never (in practical terms) needing to [defrag]("http://en.wikipedia.org/wiki/Defrag").

200mb free is less than 5% free unless you have a 40gb or smaller hard drive, according to my mental math.

(X * .05) is how much you need to keep free, where X is the total size of your hard drive.

---

### Post by inspired on 2009-10-20
Here's what df told me:
```
/dev/sda6     ext3     22G  6.4G   14G  32% /
tmpfs        tmpfs   1007M     0 1007M   0% /lib/init/rw
varrun       tmpfs   1007M  336K 1007M   1% /var/run
varlock      tmpfs   1007M     0 1007M   0% /var/lock
procbususb   usbfs   1007M  148K 1007M   1% /proc/bus/usb
udev         tmpfs   1007M  148K 1007M   1% /dev
tmpfs        tmpfs   1007M  364K 1007M   1% /dev/shm
lrm          tmpfs   1007M  2.2M 1005M   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda1  fuseblk     35G   25G   11G  71% /media/winxp
/dev/sda5     ext3     52G   50G  208M 100% /home

```
Looks like more needs clearing off... as there is less than 1% free on the /HOME

Is that likely to stop nautilus from calling up its config though?


I use Simple Backup. I don't have the drive on me right now. But can check that in a few weeks when I return home. Is that the only way to restore the settings?

Thanks,,, Jonathan

---

### Post by earthpigg on 2009-10-20
> Is that likely to stop nautilus from calling up its config though?

I don't know, to be perfectly honest.

i just know that #1 priority for you should be to free up space on /home.

once that is done (make sure you empty the trash), restart your computer and see if everything fixes itself.

if /home is not a completely functional filesystem, it is conceivable that nautilus may simply be reverting to default settings since it cannot read it's settings kept in your /home.

> 
I use Simple Backup. I don't have the drive on me right now. But can check that in a few weeks when I return home. Is that the only way to restore the settings?

if they where lost, which we don't know to be the case, and that is your only backup, then yes... as i said above, clear some space out on /home.

if you can make sense of the .xml files in this folder (hint: look for something about "places" or "bookmarks" or something else you know you have configured a certain way and see what looks or does not look familiar), then maybe you can get a sneak-peek at whether or not it will work once you free up disk space:

```
/home/ur-username/.gconf/apps/nautilus
```

that is also the folder you will want to restore once you get ahold of your backup and start digging around - assuming freeing up disk space doesn't do it, that is.


another thing to consider:
```
/dev/sda6     ext3     22G  6.4G   14G  32% /
```

given your established computer habits, you could probably reduce the size of that partition to 12gb or so, and give that 10gb to your /home partition. the only time i personally change partition schemes is on fresh installs, but you can boot an Ubuntu LiveCD and go to system -> admin -> partition editor and do that now if you wish....

...but it is always essential to have a solid backup ***immediately before*** doing anything with partitions; and you said you don't have your backup media on hand.

sooo yeah, if you wish to continue using your computer for now, i strongly suggest immediately taking measures to free up disk space.

burn some of your music/movies/etc to DVD or CD, thumb drive, something.


Usually Ubuntu does a good job of preventing you from filling a partition past 95%. most inqueres similar to yours are essentially: "Ubuntu says my disk is full but i have 5% space left on it!"... 95% is when a user ***should*** start being 'encouraged' to ask questions, not 99.8% where you are at. it appears that your CD Ripping app or something else sneaked around it. not your fault. maybe....

are you running media-related software as root on a regular basis? ie: entering your password to start your CD ripping app or something like that?

or using some media-related software ***not*** from the official Ubuntu repositories?

---

