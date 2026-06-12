---
title: "Ubuntu 8.10 Fake RAID / Powersaving issues?"
date: 2009-02-18
forum: General Help
---

### Post by jArnfield on 2009-02-18
Hi,

First of all, sorry that my first post on the forums is a request for help! Hopefully this will not be a continuing trend.

I recently installed Ubuntu 8.10 on a PC, specs as follows:

Gigabyte GA-G33-DS3R
Core 2 6600
Geforce 8800GTS with NVIDIA binary drivers (version 173)
2Gb Ram
2x 250GB drives in RAID-0 Stripe on the GRAID controller

I'm using fake RAID (dmraid?), and installed the system using the alternate disk. I'm having a few problems and I'm not sure if they're related or not.

[LIST=1]
[*]When I "restart" my PC. The RAID screen on boot (just before Grub loads) claims that the RAID array is no longer functional, or inactive. This means that grub fails to load, and produces an error. If I turn the PC off, then boot from cold, this problem doesn't exist. I can reproduce this 100%.
[*]Sometimes, rarely, the system dies all together, power is not lost, the fans and disks keep spinning, however the screen goes to black and I'm forced to turn the power off at the wall (Feels like X has crashed but Ctrl-Alt-Backspace does nothing at this point) and there doesn't seem to be any reliable feedback in the error logs, unless I'm missing something. When this happens, it is somewhat difficult to get the PC to turn back on. When I say this, I mean actually get it to post at all and get any monitor activity. This is often accompanied by a reboot cycle and continuous beeps from the system speaker on power-on. This is resolved by unplugging the power cord for a minute and trying again. More often than not the PC will boot up just fine from here on. This strange cyclic-restarting always follows a crash. It's almost like the PC power saving features have gone whacko, like it's suspended to memory, but it cannot bring itself back up. Unfortunately this is not an area I know much about. The problem felt much worse with the 177 drivers from nvidia, but this may be psychological, and I'm not even sure if this is gfx related.
[*]When looking at the system log, I have quite a few errors that read "attempt to access beyond end of device", this is on sda1, so that would be my RAID partition. Any ideas what's going on there?
[/LIST]

Any help that anyone can provide with any of the above would be very much appreciated. Apart from these hiccups, I'm completely amazed by what Ubuntu has shown.

Forgot to mention, none of this stuff happened with Windows XP while it was installed (for about a year?), this PC is probably the most stable I have owned.

Cheers
John

---

### Post by jArnfield on 2009-02-28
Anybody?

See, I waited patiently before bumping! That must earn me a few brownie points :P

---

### Post by fjgaude on 2009-02-28
It's very difficult to analyze what might be going on with your setup. Could be a poor power supply, loose connections to the drives, etc.

You have two drives in BIOS raid0 and you boot Ubuntu from a partition on one of them? Or you are booting through **grub** on raid0?

Show us what **df -m** looks like.

Let us know how you are doing.

---

### Post by jArnfield on 2009-02-28
Hi,

Thanks, this is the output from "df -m"
```
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/mapper/isw_bchgedheic_Volume01
                        463670     23709    416408   6% /
tmpfs                     1004         0      1004   0% /lib/init/rw
varrun                    1004         1      1004   1% /var/run
varlock                   1004         0      1004   0% /var/lock
udev                      1004         3      1002   1% /dev
tmpfs                     1004         1      1004   1% /dev/shm
lrm                       1004         3      1002   1% /lib/modules/2.6.27-11-generic/volatile
Atomserver:/srv/media
                        466597    227132    215763  52% /media/media

```
As far as I know, grub exists on the raid 0 array. Prior to installing ubuntu, I created a single raid 0 span across 2 disks. No other disks/partitions to note. Ubuntu was then installed on top of this. To my surprise, the system works fine depending on whether they're plugged into the GRAID controller or Intel controller. I assume this just means that Linux software RAID really isn't at all dependent on the hardware in any way.

The problem seems to have settled down a little lately. The power supply explanation does sound reasonable, but it's an Enermax 450W jobby and I wouldn't imagine the hardware I have should cause it many problems, but you never know.

I've also jiggled my SATA cables around prior to posting the first message lol. They're the old style non-latching ones with the cruddy connectors that always fall out, but I'm fairly certain that they're not the problem.

I hope this answers your question :confused:

---

### Post by Slim Odds on 2009-02-28
I would highly recommend ditching the fakeRAID and just use software RAID.

I have a Soyo motherboard that has fakeRAID and I found it to be a huge headache. I switched to plain old software RAID and it works great.

I used the alternate install CD, which has mdadm.  I created a small boot partition on one drive and a small swap on the other. Then I created duplicate partitions for /, /usr, /tmp, /var and /home on each drive. Then used mdadm to join them.

The one trick is that the mdadm stuff in the partitioner does **NOT** show up until you've partitioned some RAID partitions.

---

### Post by fjgaude on 2009-02-28
Okay,  you have, through the use of alternate CD install and using dmraid Ubuntu installed on a BIOS created fakeRAID. Wow! and it works most of the time. Few have done this but I suppose the developers have made it work one way or the other.

If it works most of the time I'd try to see if hardware issues are present.

You will not be able to boot from an **mdadm** raid0, but can from raid1. So many things come into play... you go the raid0 route for quickness, eh?

Here's a good link to learn of the features of various raid arrays:

[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)

Keep us informed of your doings. Thanks!

---

