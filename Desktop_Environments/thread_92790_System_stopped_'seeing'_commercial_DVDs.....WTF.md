---
title: "System stopped 'seeing' commercial DVDs.....WTF"
date: 2005-11-20
forum: Desktop Environments
---

### Post by stdoubt on 2005-11-20
**[COLOR="Red"]I have recently played a commercial DVD with xine[/COLOR].**

After viewing, I closed xine. Unmounted the DVD (icon).
Ejected the DVD (right-click menu).

Then I installed xmms; listened to some mp3s; surfed;
then maybe rebooted. Now I try to play the SAME DVD,
but the system won't even recognize the disk.

NOTE: -->   **"Home-made" DVDs still work fine!**
	(data AND 'rips')
> 
$ sudo hdparm /dev/hdd
/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

When I try to play any of my commercial disks (I have 4, all
Firefly TV series. That's my only commercial DVDs),
**Kaffeine** says:
> 
The source can't be read.

Maybe you don't have enough rights for this, or source
doesn't contain data (e.g: no disk in drive). (/dev/dvd)

**Xine** says:
> 
There is no input pluging to handle 'dvd:/'.
Maybe MRL syntax is wrong or file/stream source doesn't exist.

The source can't be read.

Maybe you don't have enough rights for this, or source
doesn't contain data (e.g: no disk in drive). (/dev/dvd)

$ sudo mount /dev/hdd
mount: No medium found
$ sudo mount /dev/dvd
mount: No medium found

NOTE: This disk is recognized perfectly in my other system (Fedora).
**It's not the disk.......**
**It's not the DVD player.....**(unless SONY remotely hacked its firmware)!
**It MUST be software related?**????

What I have installed that may be related:
[B]dvd+rw-tools		              
gstreamer0.8-dvd
libdvdcss2		                  
libdvdcss2-dev
libdvdnav4		                 
libdvdplay0
libdvdna-dev		                 
xine-ui
libdvdplay0-dev	                        
libdvdread3
libdvdread3-dev	                           
ogle-mmx
okle			                       
kaffeine-xine
kaffeine		                       
libxine-dev
libxine1c2		                  
libxinerama1
w32codecs[/B]

$ dmesg | tail
> 
ATAPI device hdd:
[4370477.558000]   Error: Not ready -- (Sense key=0x02)
[4370477.558000]   Incompatible medium installed -- (asc=0x30, ascq=0x00)
[4370477.558000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4370477.558000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4370477.838000] ATAPI device hdd:
[4370477.838000]   Error: Not ready -- (Sense key=0x02)
[4370477.838000]   Incompatible medium installed -- (asc=0x30, ascq=0x00)
[4370477.838000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4370477.838000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
****
I have never had so much trouble with DVD playback!
**This is getting ridiculous**. Please someone throw me
a clue!
P.S. ~ I'm not willing to try 'regionset' since I've never had to
in the past, and don't want to risk borking my drive.

---

### Post by WirelessMike on 2005-12-01
Try changing the source in those apps from /dev/dvd to /dev/hdd where your dvd is actually mounted.  /dev/dvd is a sybolic link defined in the /dev directory to a mount point in your /etc/fstab file.

If that works, go to your /etc folder and ls -la

See what dvd points to.  It should be a symbolic link to hdd.  If it's not, there's your problem.

I have 2 dvd players.  The master /dev/hda is recognized also as /dev/dvd, but the slave /dev/hdb, which used to be recognized on mount, is no longer, and i have to actually tell kaffeine to mount /dev/hdb, or mount kaffeine from the hdb.  Not sure what config ruined my run of excellent automounting, but even telling these players to mount /dev/dvd1 doesn't really seem to get me back where I was.  I feel I'm close to a solution for my problem, though.  However--  If anyone else has a similar problem or solution...

---

