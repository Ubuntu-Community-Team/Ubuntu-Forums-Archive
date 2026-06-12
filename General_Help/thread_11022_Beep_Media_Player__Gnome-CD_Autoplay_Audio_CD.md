---
title: "Beep Media Player / Gnome-CD Autoplay Audio CD"
date: 2005-01-13
forum: General Help
---

### Post by ayam on 2005-01-13
**My Problem**

The expected result of inserting an audio CD, when running Ubuntu, is that Gnome-CD opens up and plays the CD. I cannot get  my audio CDs to play on Gnome-CD, hence not being able to autoplay. Beep-Media-Player has no problems playing my audio CDs but I cannot autoplay.

Is it  possible to get them to autoplay on Beep Media Player, therefore needing to know the the command line to insert into 
Computer>Desktop Preferences>Removable Storage

If this is not possible, then how can I get my audio cds to play on Gnome-CD?

**My Computer Configuration**

12X Matshita SCSI CD-ROM (used to play audio cds and connected to my sound card)
40X 16X 10X Yamaha SCSI CD-ROM 

Both are connected on the same cable to the same Adaptec 2920 SCSI card.

Ubuntu detected the Matshita as /dev/scd0 and the Yamaha as /dev/scd1 for /etc/fstab/ . These were both wrong  and "dmesg" revealed that the the CD-ROM drives were meant to be /dev/sr0 and /dev/sr1 respectively. Making these changes on /etc/fstab made it possible for my data CDs to be automatically mounted etc.

**My attempts to get  Gnome-CD to play an audio CD**
The audio CD does not play when I change the  description in Gnome-CDs preference menu from /dev/cdrom to /dev/sr0. The audio does play when I make the same changes in Beep Media Player

Gnome CD _does play_ my audio CD WHEN I have the CD playing in Beep Media Player with both programmes having the /dev/cdrom preference changed to /dev/sr0

ie. 1) Insert audio CD
2) Start Beep Media Player > Play CD
3) Start Gnome-CD player 
4) Gnome CD player shows the track progressing


Thanks

---

### Post by dkuhlman on 2005-01-13
I have the same problem and symptoms.  CD Player recognizes the CD and displays the names of the songs.  The progress slider moves along, but there is no sound.

The esd daemon is running.

```
~ [31] ps aux | grep esd
dkuhlman  3908  0.0  0.1  1964  608 ?        Ss   07:53   0:00 /usr/bin/esd -terminate -nobeeps -as 2 -spawnfd 17
dkuhlman 11149  0.0  0.0  1540  492 pts/4    S+   14:52   0:00 grep esd

```

Does CD Player use esd?  Do I need to configure it?

I can play sound off the Internet with RealPlayer.  So, my sound is working for some applications.

What else do I need to install or configure for the Gnome CD Player (gnome-cd)?

Thanks in advance?

Dave

---

