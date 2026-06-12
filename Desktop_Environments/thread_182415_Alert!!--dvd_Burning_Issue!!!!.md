---
title: "Alert!!--dvd Burning Issue:!!!!"
date: 2006-05-26
forum: Desktop Environments
---

### Post by an10ae on 2006-05-26
ALERT!!--DVD BURNING ISSUE:!!!!

People are no longer able to burn DVDs after upgrading.
Or at least reliably burn them.:confused: 

It would seem to be a common issue people are having.
Below are some of the other threads dealing with this issue.
I propose a new common thread creation. Come on people let's 
get this resolved.

I myself have been struggling for a while with it.
You can see what I've tried thus far here.

[http://www.ubuntuforums.org/showthread.php?t=179846](http://www.ubuntuforums.org/showthread.php?t=179846)

Some other threads
[http://www.ubuntuforums.org/showthread.php?t=182300](http://www.ubuntuforums.org/showthread.php?t=182300)
[http://www.ubuntuforums.org/showthread.php?t=181577](http://www.ubuntuforums.org/showthread.php?t=181577)
[http://www.ubuntuforums.org/showthread.php?p=1053704](http://www.ubuntuforums.org/showthread.php?p=1053704)

Sort of the same issue (maybe?)
[http://www.ubuntuforums.org/showthread.php?t=181985](http://www.ubuntuforums.org/showthread.php?t=181985)

I've also found this in LaunchPad, it would seem a bug report has been filed.

[https://launchpad.net/distros/ubuntu/+bug/32966](https://launchpad.net/distros/ubuntu/+bug/32966)

Here is the rundown.

I can burn CDs successfully and read them.
I can Burn DVDs with no errors but they are coasters.
I can burn DVDs which are good from a live cd such as (PCLinuxOS)

**With DMA Disabled growisofs gives this error:**

ant@ebuntu:~$ growisofs -Z /dev/hdc -R -J /home/ant/testburn
[COLOR="Red"]:-[ READ DISC INFORMATION failed with SK=3h/ASC=57h/ACQ=00h]: Input/output error[/COLOR]
ant@ebuntu:~$ growisofs -Z /dev/hdc -R -J /home/ant/testburn
Executing 'mkisofs -R -J /home/ant/testburn | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO: UTF-8 character encoding detected by locale settings.
Assuming UTF-8 encoded filenames on source filesystem,
use -input-charset to override.
/dev/hdc: "Current Write Speed" is 4.1x1385KBps.
0.98% done, estimate finish Thu May 25 14:21:23 2006
1.96% done, estimate finish Thu May 25 14:09:28 2006
2.94% done, estimate finish Thu May 25 14:04:57 2006
3.92% done, estimate finish Thu May 25 14:03:06 2006
...
...
...
98.79% done, estimate finish Thu May 25 13:57:29 2006
99.77% done, estimate finish Thu May 25 13:57:29 2006
Total translation table size: 0
Total rockridge attributes bytes: 270
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 21000
511201 extents written (998 MB)
builtin_dd: 511216*2KB out @ average 3.7x1385KBps
/dev/hdc: flushing cache
/dev/hdc: closing track
/dev/hdc: closing session
/dev/hdc: reloading tray

**The disk is then unreadable.**

ant@ebuntu:~$ mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

**With DMA Enabled growisofs gives no error:**

ant@ebuntu:~$ growisofs -Z /dev/hdc -R -J /home/ant/testburn
Executing 'mkisofs -R -J /home/ant/testburn | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO: UTF-8 character encoding detected by locale settings.
Assuming UTF-8 encoded filenames on source filesystem,
use -input-charset to override.
/dev/hdc: "Current Write Speed" is 4.1x1385KBps.
0.98% done, estimate finish Thu May 25 14:21:23 2006
1.96% done, estimate finish Thu May 25 14:09:28 2006
2.94% done, estimate finish Thu May 25 14:04:57 2006
3.92% done, estimate finish Thu May 25 14:03:06 2006
...
...
...
98.79% done, estimate finish Thu May 25 13:57:29 2006
99.77% done, estimate finish Thu May 25 13:57:29 2006
Total translation table size: 0
Total rockridge attributes bytes: 270
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 21000
511201 extents written (998 MB)
builtin_dd: 511216*2KB out @ average 3.7x1385KBps
/dev/hdc: flushing cache
/dev/hdc: closing track
/dev/hdc: closing session
/dev/hdc: reloading tray

**However the disk is still unreadable.**

ant@ebuntu:~$ mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

**dmesg says the following about the device.**

[4294784.992000] cdrom: This disc doesn't have any tracks I recognize!
[4294847.012000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294847.012000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4294847.012000] ide: failed opcode was: unknown
[4294847.018000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4294847.076000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294847.076000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4294847.076000] ide: failed opcode was: unknown
[4294847.076000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4294847.102000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294847.102000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4294847.102000] ide: failed opcode was: unknown
[4294847.108000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4294847.114000] cdrom: This disc doesn't have any tracks I recognize!
[4294847.138000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294847.138000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4294847.138000] ide: failed opcode was: unknown
[4294847.144000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4294869.862000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4294869.862000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4294869.862000] ide: failed opcode was: unknown
[4294869.862000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4294931.980000] cdrom: This disc doesn't have any tracks I recognize!
[4295188.653000] hdc: irq timeout: status=0xd0 { Busy }
[4295188.653000] ide: failed opcode was: unknown
[4295188.653000] hdc: DMA disabled
[4295188.803000] hdc: ATAPI reset complete
[4295209.616000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295209.616000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295209.616000] ide: failed opcode was: unknown
[4295209.622000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295209.658000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295209.658000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295209.658000] ide: failed opcode was: unknown
[4295209.664000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295209.765000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295209.765000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295209.765000] ide: failed opcode was: unknown
[4295209.765000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295209.796000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295209.796000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295209.796000] ide: failed opcode was: unknown
[4295209.802000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295209.823000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295209.823000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295209.823000] ide: failed opcode was: unknown
[4295209.829000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295209.870000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4295209.870000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4295209.870000] ide: failed opcode was: unknown
[4295209.870000] end_request: I/O error, dev hdc, sector 64
[4295209.870000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[4295211.773000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295211.773000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295211.773000] ide: failed opcode was: unknown
[4295211.774000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295211.800000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295211.800000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295211.800000] ide: failed opcode was: unknown
[4295211.806000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295211.812000] cdrom: This disc doesn't have any tracks I recognize!
[4295211.837000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295211.837000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295211.837000] ide: failed opcode was: unknown
[4295211.843000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295212.768000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295212.768000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295212.768000] ide: failed opcode was: unknown
[4295212.768000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295212.834000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295212.834000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295212.834000] ide: failed opcode was: unknown
[4295212.835000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295212.865000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295212.865000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295212.865000] ide: failed opcode was: unknown
[4295212.871000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295212.929000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295212.929000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295212.929000] ide: failed opcode was: unknown
[4295212.935000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295212.941000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4295212.941000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4295212.941000] ide: failed opcode was: unknown
[4295212.941000] end_request: I/O error, dev hdc, sector 64
[4295212.941000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[4295214.325000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295214.325000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295214.325000] ide: failed opcode was: unknown
[4295214.326000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295214.391000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295214.391000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295214.391000] ide: failed opcode was: unknown
[4295214.392000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295214.423000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295214.423000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295214.423000] ide: failed opcode was: unknown
[4295214.429000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295214.484000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295214.484000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295214.484000] ide: failed opcode was: unknown
[4295214.490000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295214.496000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4295214.496000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[COLOR="Red"][4295214.496000] ide: failed opcode was: unknown
[4295214.496000] end_request: I/O error, dev hdc, sector 64[/COLOR]

**Hdparm say this about the Drive**

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 [COLOR="Red"]HDIO_GETGEO failed: Invalid argument[/COLOR]

Please Gurus! come to the rescue!

---

### Post by psylence on 2006-05-26
Did you try the solution here? [http://www.ubuntuforums.org/showthread.php?t=182300](http://www.ubuntuforums.org/showthread.php?t=182300)

Not going to read through all those :)

---

### Post by an10ae on 2006-05-26
Thank you. 
psylence
Yes I did but it did not resolve the issue for me.

I've also found this in LaunchPad it would seem a bug report has been filed.

[https://launchpad.net/distros/ubuntu/+bug/32966](https://launchpad.net/distros/ubuntu/+bug/32966)

---

### Post by an10ae on 2006-05-26
The pile of coasters grows!!!!!!](*,) ](*,)

---

### Post by vyruss on 2006-05-26
Yes, I have this issue too, but with BOTH K3B and Gnomebaker.

Filed as bug #37876 in Launchpad. I'm afraid this is going to make it into Dapper and people like us will continue to have trouble.

---

### Post by nalmeth on 2006-05-26
My DVD burner is busted, so I can't confirm or deny this on my side.

This must be worked out ASAP if it's so widespread

---

### Post by an10ae on 2006-05-26
I have not tried dapper from a fresh install. This appears to be mainly those of us who have been goining the dist-upgrade route. Now that Dapper is a "live cd " I will Download the RC and see what's up.

---

### Post by ericesque on 2006-05-26
...and making headlines today, apparently the Ubuntu community has amassed a pile of coasters today-- the likes unseen outside of AOL's free minutes disk pressing center where 100% of all cds and dvds burned are in fact coasters.

---

### Post by an10ae on 2006-05-26
BAD NEWS GUYS...:( 

I just downloaded Dapper RC.
Booted from the live cd. Installed k3b and am having the same problems from within the liveCD environment.:confused: 

I tried burning a data DVD from K3b. No errors. Disk Unreadable.
I tried from the commandline with growisofs. No errors. Disk Unreadable.

This is not a dist-upgrade issue it is in Dapper RC.](*,) 

Similar output within the LiveCD Envirinment.

hdparm

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 [COLOR="Red"]HDIO_GETGEO failed: Invalid argument[/COLOR]


dmesg

[4295320.986000] cdrom: This disc doesn't have any tracks I recognize!
[4295321.150000] cdrom: This disc doesn't have any tracks I recognize!
[4295321.187000] cdrom: This disc doesn't have any tracks I recognize!
[4295323.013000] cdrom: This disc doesn't have any tracks I recognize!
[4295602.038000] cdrom: This disc doesn't have any tracks I recognize!
[4295889.809000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295889.809000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295889.809000] ide: failed opcode was: unknown
[4295889.815000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295890.549000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295890.549000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295890.549000] ide: failed opcode was: unknown
[4295890.555000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295890.583000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295890.583000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295890.583000] ide: failed opcode was: unknown
[4295890.583000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00
[4295890.589000] cdrom: This disc doesn't have any tracks I recognize!
[4295890.620000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4295890.620000] hdc: packet command error: error=0x30 { LastFailedSense=0x03 }
[COLOR="Red"][4295890.620000] ide: failed opcode was: unknown
[4295890.621000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x57  ascq: 0x00[/COLOR]

I would believe this to be an issue with growisofs. 
growisofs is a part of the dvd+rw-tools package.

cdrecord is working fine.  

I know k3b uses growiofs for DVD burning and would assume the other apps do too.
So it's not k3b, Gnomebaker.

It could either be a change in the way DMA is being recognised and used or a change in the way growisofs is working. (perhaps not closing the disk properly?)

---

### Post by dglock on 2006-05-26
I can confirm this but its even worse on kbuntu, k3b will not burn and reports errors and then hangs at flushing the cache.  It locks the burner drawer and i have to reboot to get the dvd out.  This is very bad!

don

---

### Post by fred.cpp on 2006-05-26
Yesterday night afther dist-upgrade I couldn't burn a CD with nautilus, No errors, just a stoped progress bar.
I had to do It from windows :(

---

### Post by eeclark on 2006-05-26
I would imagine that this would need to get resolved quick to make the release deadline...right?

---

### Post by nix4me on 2006-05-26
Hope so.

nix4me

---

### Post by BoyOfDestiny on 2006-05-26
Just curious, have you guys tried burning at a lower speed?

---

### Post by an10ae on 2006-05-26
BoyOfDestiny,
  
 Hi, Yes I have tried multiple methods of burning the disk. Gui, Commandline, different speeds, DMA on, DMA off.

I've been making changes trying different things and trying to document everything along the way. All to no avail. I really believe that this needs the attention of some higher level folks than myself.

---

### Post by richbarna on 2006-05-26
Just a question, are ANY of you using the KDE environment ?
It's just after so much hassle with gnome I switched.
I installed kubuntu 5.10
upgraded to Dapper
Just been listening to my cd collection on xmms while burning dvd's on k3b.
Everybody I see who posts on the forum with sound or video or burning problems is using Gnome.
I still have no idea why it gets recommended to newbies. It seems to be a non stop headache.
I have far less problems with KDE.

---

### Post by an10ae on 2006-05-26
It doesn't matter what environment I'm in.
I pretty much stay in Enlightenment DR17 for my window manager and use a mix of gnome and kde apps.
It's not a KDE or GNOME Thing. It's an issue with growisofs or how the kernel is using DMA. 
K3B is a kde app.

---

### Post by richbarna on 2006-05-26
Ok, here's the thing, I installed the server install.
Added the ubuntu-desktop, major problems with dvd and cd drives playing, burning etc.
Removed Gnome, installed KDE all works.
Maybe I'm just lucky.

Back in ubuntu 5.10 amarok was a no go with Gnome.
Installed KDE and guess what ?

What about the various libs and dependencies that come with kde but not Gnome?

Like I said maybe I was lucky, but then so were 4 of my friends who did the same thing after having media problems with gnome.

I've got enlightenment on one of my laptops, nice choice.

And, thanks for pointing out that K3B is a KDE app, I will be able to sleep better tonight knowing that.

---

### Post by disturbed1 on 2006-05-26
Scared me at first. But I can report that DVD burning is not an issue on my systems.

2x Nforce 3 chipset (Pioneer A05, LG 4166b)
Intel i850 chipset (Pioneer A03)
VIA KT133A (Nec 2500)

Not a single QT library/app on any of my systems.

Created data discs with both Gnome Baker and with Nautilus, did the same with DVD ISOs. No problems what so ever.

Honestly, I'd look into cheap media, failing DVD burners, hacked firmware. Something along those lines.

---

### Post by an10ae on 2006-05-27
richbarna,
I appreciate your input. I do but, in order to fix the problem in ubuntu I don't feel that uninstalling GNOME is the answer as ubuntu is a GNOME based distro and is the distro I want to use not kubuntu. As far as having KDE Installed I do so it can't be a dependency issue. I have and have had KDE (complete kubuntu-desltop) and GNOME both installed as I like a lot of KDE apps (konqueror, amarok, kaffeine), but I prefer the standard ubuntu utilities (Synaptic, Gedit, Printers and on and on....).
disturbed1,
I'm glad to hear that not everyone is affected by this but, many of us are and it has been confirmed multiple times (Several threads and confirmations, and at least 2 bug reports in launchpad). point being the issue exists and needs resolution. Please read the initial post. It's not the hardware or media as both work fine in any other liveCD distro.

What I'm looking for here is someone better versed than I am in diagnosing these problems. Someone to ask the right questions and or give real information about the questions I have asked.

Not ubuntu breaking suggestions. 
Not denials of the problem.

I mean no offense and only want this to get somewhere. A realistic suggestion of something to **do**  would greatly be appreciated.

---

### Post by disturbed1 on 2006-05-27
[http://www.ubuntuforums.org/showthread.php?t=179846]("http://www.ubuntuforums.org/showthread.php?t=179846") <--- Purely media error. The Toshiba drive has a strick firmware that only allows certian media with a propper media ID to burn at full speed. Let's take Taiyo Yuden DVD-R 8x media. This media will have a MID of TYG-02. Other companies with clone/fake this MID to allow their cheaper media to be seen as a higher speed/higher quality media. The burner attempts to burn at this speed, and you will recieve errors. The same can be said with CD media.

[http://www.ubuntuforums.org/showthread.php?t=182300]("http://www.ubuntuforums.org/showthread.php?t=182300") did not have burn proof turned on. Once corrected, the issue was resolved.

[http://www.ubuntuforums.org/showthread.php?t=181577]("http://www.ubuntuforums.org/showthread.php?t=181577") not enough information to correctly see the problem, however, was told how to correctly lower the speed, and burning was fine.

[http://www.ubuntuforums.org/showthread.php?p=1053704]("http://www.ubuntuforums.org/showthread.php?p=1053704") hardware error, plain and simple. Installed Nero, installed this, canceled that, tried this. Foobar'd system, went to reinstall, foobar'd system again. Reinstalled **Breezy,** drive did not read blank media.

For you, I would enable burn proof, and make sure everything else is idle at the time of burning.

And how about some hardware details.
DVD Drive + firmware version
Motherboard Chipset
Media attempting to use.

Check out this place DVD Hardware related info
[http://club.cdfreaks.com/](http://club.cdfreaks.com/)

---

### Post by vyruss on 2006-05-27
[QUOTE=disturbed1]...[/QUOTE]

Thanks for your advice, but it is clearly not the media or the drive's fault, as everything works fine in Breezy and Windows.

---

### Post by viraptor on 2006-05-27
Confirming with:
HL-DT-ST DVD-RW GWA-4040N
It worked in 5.10, after updating to 6.06 LTS it destroys dvds. I can record anything (growiso, or from iso file) without errors during recording, but disks are NOT readable after it. Iso file is correct and can be mounted through loop device.
Tried gnomebaker and commandline - same effect. I can read almost any 100-block part (sometimes after 2-5'th try) of DVD with dd, and it's the same as .iso, but at larger parts it gets stuck.
Other DVDs are readable.
Lower speed settings don't help. (anyway - it worked as x4 before, so it has to now)

If someone filled a bug for this issue (upgrading to dapper one!) please point me to correct launchpad id.
Other people - please try your dvds and report errors ASAP, as developers should really treat it as a show-stopper now!

Edit: Burnfree is on in confs.

---

### Post by airmaniac on 2006-05-27
When having read this thread, I tried saving my /home (1 GB) on DVD+R at once - absolutely no problem using

- HL-DT-ST DVD-RAM GSA-4081B
- GnomeBaker 0.5.1
By the way, DVD-RAM works as well.

System is Dapper Drake RC, latest updates installed.

Sorry and good luck to you

Uli

---

### Post by ketsugi on 2006-05-27
For what it's worth, I'm having NO trouble burning DVDs in Dapper.

Using a Sony DRU-510A in an external USB enclosure, through a USB2.0 PCMCIA card (my laptop only has USB1.1), using Bonfire (which is basically a GTK frontend to growisofs and mkisofs). I burn an md5sum digest of hashes with each disc, and check the md5s later. No errors.

---

### Post by viraptor on 2006-05-27
Tried cdrecord-prodvd 2.01b31 for a change - still the same effect. Recording was complete without errors, but when mounting:
```
[4303301.756000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4303301.756000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4303301.756000] ide: failed opcode was: unknown
[4303301.756000] end_request: I/O error, dev hdc, sector 0
[4303301.756000] Buffer I/O error on device hdc, logical block 0
```
With different sectors - 0, 16, 24, 32 mostly.

Any other ideas as what to try next?
Maybe how can I force installation of Breezy's version of dvdtools to check if it gets back to normal state?

---

### Post by dglock on 2006-05-27
[QUOTE=ketsugi]For what it's worth, I'm having NO trouble burning DVDs in Dapper.

Using a Sony DRU-510A in an external USB enclosure, through a USB2.0 PCMCIA card (my laptop only has USB1.1), using Bonfire (which is basically a GTK frontend to growisofs and mkisofs). I burn an md5sum digest of hashes with each disc, and check the md5s later. No errors.[/QUOTE]

  I have that same problem using my sony ide burner but not with my sony external usb 2 burner!

  Both k3b and nero work fine in the usb burner but will not burn with the ide drive. This problem is in both my kbuntu and ubuntu installed rc versions.

  don

---

### Post by magisterludi on 2006-05-28
Burning doesn't here work either. Tried internal and external. Is there a malone for it?

---

### Post by mcpish on 2006-05-28
I just installed a fresh copy of Dapper Drake last night and I'm not having any problems recording DVDs.  I'm using K3B and it works perfectly.  I have a toshiba model DVD-R drive if that helps?

---

### Post by viraptor on 2006-05-28
I didn't find any bugs for exactly this issue, so I filled
[https://launchpad.net/distros/ubuntu/+source/dvdrtools/+bug/46966](https://launchpad.net/distros/ubuntu/+source/dvdrtools/+bug/46966)
but now I'm not sure if it's dvdrecord's issue. I tried cdrecord-prodvd with the same results. Now I'm trying other things -> kernel, controller settings, no background load, etc.
If anyone has some suggestions for other things to try -> please write them. I'm running out of ideas and blank dvds ;)

---

### Post by an10ae on 2006-05-28
Great Viraptor This definitely needs the attention of the devlopers I think. I wish I could be more help but, I am a mere mortal who is completely out of ideas.

---

### Post by towsonu2003 on 2006-05-28
I think it would be much better of an idea to input your comments to [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37876/+index](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37876/+index)  ? This would make devels work faster for it? I found if number of subscribers to a bug goes up, it is fixed faster. ;)

---

### Post by Lovechild on 2006-05-28
burning bug I reported for Fedora - will also apply to Ubuntu Dapper.. notice the amount of affected users.. this is an LTS showstopper.

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=179862](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=179862)

---

### Post by viraptor on 2006-05-28
Hmmm... I got something simmilar to:
```
cdrecord: Success. mode sense g1: scsi sendcmd: no error
CDB:  5A 00 30 00 00 00 00 00 08 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 8
cmd finished after 0.008s timeout 40s
```
(from attached ltrace in your bug report) trying dummy mode writing lately, but it didn't happen every time. I'll try to reproduce it and attach report, if it'll happen in real mode - maybe it has some connection with this issue (or is a separate one...)

---

### Post by viraptor on 2006-05-29
Ok - you can probably use your "broken" dvds.
I can read them without problems on my other dvd - but still they are written in a way that prevents them from being read on *any* os running on the box where I burned those disks. (dvd reader problem)
Still not able to tell whether it's read or write issue, but now, not being able to read it under any os/kernel combination on the original box, I think it's writing problem.

---

### Post by vyruss on 2006-05-29
[QUOTE=viraptor]Ok - you can probably use your "broken" dvds.
I can read them without problems on my other dvd - but still they are written in a way that prevents them from being read on *any* os running on the box where I burned those disks. (dvd reader problem)
Still not able to tell whether it's read or write issue, but now, not being able to read it under any os/kernel combination on the original box, I think it's writing problem.[/QUOTE]

I get exactly the same here, viraptor. And what's even stranger, Nero Linux does exactly the same thing as GnomeBaker and K3B, so unless it uses growisofs (which I doubt) this is quite a bug!

And let me repeat, everything worked just fine in Breezy, Dapper broke it.

---

### Post by mcpish on 2006-05-29
I've actually noticed that Dapper has actually "fixed" a minor issue with DVD-R burning for me in k3b.  

In Breezy, k3b didn't report any status info on my DVD-R drive's "FIFO buffer" while burning DVDs (it only did so for burning CDs for some reason).  But now the status bar is fully active, and gives me a good realtime indication of the buffer during recording.

---

### Post by nemesa on 2006-05-30
Why this bug isn't confirmed on launchpad? I think it could be really important...

---

### Post by viraptor on 2006-05-30
I don't think anybody decided yet what's the source of problem, so they don't confirm it.
Kernel guy wrote, it's not in kernel (not fs reading / mounting at least), and dvdrtools guys didn't write anything. But really it's probably not dvdrtools issue, as nero and cdrecord-prodvd do the same thing and probably not kernel / fs driver as dvd can't be mounted on the same machine on previous kernels as well. I'd risk saying it's current kernel / ide writing issue - I'm trying to verify that lately...

---

### Post by an10ae on 2006-05-31
Has anyone had any headway on this?
Is the release happening tomorrow/tonight?

---

### Post by makro on 2006-05-31
I've had a similar problem with iso cd burning

try this

```

sudo modprobe -r ide-cd
sudo modprobe ide-scsi

```

and then re-open gnomebaker or similar and try to burn.. it has worked for me!!

If it works
add ide-cd to /etc/modprobe.d/blacklist
add ide-scsi to /etc/modules

to keep the settings on reboot.

Let me know if it works

---

### Post by an10ae on 2006-05-31
Makro
Thanks for the input but, it didn't work here. Seemed like a good idea though.

---

### Post by Haegin on 2006-06-02
I noticed several people are having problems with HL-DT-ST drives. I have a HL-DT-ST DVDRAM GSA-4167B drive from LG which should be able to write most media (and has definatly written DVD-R from the same batch I'm using now) so could it be a problem with HL-DT-ST drives?

Also I remember reading somewhere when calling cdrecord directly from the terminal that the current version of cdrecord does not support dvd-r media. I have not tried with dvd+r as I have none but it may be worth checking that out.

I have already burnt several dvds (on dvd-r media from the same batch as the ones that are currently failing) but they were all on breezy so it seems a problem has occured with the new version. I'm going to try and downgrade cdrecord and growisofs - will report back later.

---

### Post by dglock on 2006-06-02
[QUOTE=Human Prototype]I noticed several people are having problems with HL-DT-ST drives. I have a HL-DT-ST DVDRAM GSA-4167B drive from LG which should be able to write most media (and has definatly written DVD-R from the same batch I'm using now) so could it be a problem with HL-DT-ST drives?

Also I remember reading somewhere when calling cdrecord directly from the terminal that the current version of cdrecord does not support dvd-r media. I have not tried with dvd+r as I have none but it may be worth checking that out.

I have already burnt several dvds (on dvd-r media from the same batch as the ones that are currently failing) but they were all on breezy so it seems a problem has occured with the new version. I'm going to try and downgrade cdrecord and growisofs - will report back later.[/QUOTE]


  In my case its the ide burner that won't work. Its a sony and so is my usb drive which works fine with both k3b and nero. 

don

---

### Post by dglock on 2006-06-02
[QUOTE=Human Prototype]I noticed several people are having problems with HL-DT-ST drives. I have a HL-DT-ST DVDRAM GSA-4167B drive from LG which should be able to write most media (and has definatly written DVD-R from the same batch I'm using now) so could it be a problem with HL-DT-ST drives?

Also I remember reading somewhere when calling cdrecord directly from the terminal that the current version of cdrecord does not support dvd-r media. I have not tried with dvd+r as I have none but it may be worth checking that out.

I have already burnt several dvds (on dvd-r media from the same batch as the ones that are currently failing) but they were all on breezy so it seems a problem has occured with the new version. I'm going to try and downgrade cdrecord and growisofs - will report back later.[/QUOTE]


  In my case its the ide burner that won't work. Its a sony and so is my usb drive which works fine with both k3b and nero. 

don

---

### Post by Haegin on 2006-06-02
Ok, I have managed to burn a dvd using XCDRoast (available on the repos) using cdrecord-prodvd. Instructions below:

1. Go here ([ftp://ftp.berlios.de/pub/cdrecord/ProDVD/](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/)) and download "cdrecord-prodvd-2.01b31-i686-pc-linux-gnu"
2. Rename it to "cdrecord.prodvd"
3. ```
sudo cp cdrecord.prodvd /usr/lib/xcdroast/bin
```
4. Set cdrecord.dvdpro to be executable ```
sudo chmod a+x /usr/lib/xcdroast/bin/cdrecord.prodvd
```
5. Run xcdroast as root and set it all up.
6. When you get to the part asking for a prodvd key paste the one from [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/README](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/README) (without the "CDR_SECURITY=" bit)
7. Save configs and exit
8. You should now be able to use xcdroast to burn your dvds/cds and other stuff (though it is a slightly confusing interface and I cant find how to burn .iso images)

Hope this helps until the devs clear up the problems with k3b...

---

### Post by Haegin on 2006-06-03
In my opinion (and I'm willing to try and test this to confirm it) there is a bug in growisofs (in dvd+rw-tools) which is used by many programs on linux to burn DVDs.

The only program I know of that doesn't use growisofs is xcdroast which uses cdrecord-ProDVD to write to dvd. This is not GPL so won't please some people but it is useable as a temporary fix (see my previous post).

Hope this helps somebody track down and fix the problem, now I'm off to see if I can compile dvd+rw-tools from source...

EDIT: Tried and failed - it's not a normal .configure, make, sudo checkinstall run and I don't have enough experience to be able to work it out.

---

### Post by Haegin on 2006-06-03
Sorry to triple post but I can confirm it is a problem with the ubuntu version of dvd+rw-tools and that it is easily fixable (worked for me anyway).

Firstly, **if it ain't broke, don't fix it!** If you can already burn dvds then don't fiddle with it (unless you have a really good reason).

If you do have a problem:

1. Download the appropriate deb file for your architecture (click on the name of your architecture to download it)
[http://packages.debian.org/unstable/utils/dvd+rw-tools](http://packages.debian.org/unstable/utils/dvd+rw-tools)
(I downloaded i386 and that worked for me)

2. Install it
[code] sudo dpkg -i <path to the file you downloaded>

3. Restart your burning program if neccessary.

4. Enjoy....

---

### Post by -deadcats on 2006-06-03
Thanks for all the detective-work! I've got the same problem you have. With the new libraries installed, I'm ready to test out your solution. Again, thanks for all the hard work. :)

regards,
-dc

---

### Post by Rondonjin on 2006-06-03
This thread had me worried but I just tried burning a DVD with Graveman and it worked perfectly. I have a GSA-4120B unit in my machine. This was a fresh install of Dapper from the RC and updated after installation.

Wayne

---

### Post by mpierce on 2006-06-03
I had a problem with k3b and then tried gcombust - same problem; permission was denied. However, I was able to burn as root. I then changed owner of both /dev/scd0 and /dev/sg1 to root.cdrom (cdrom is my burning group) and viola, everything worked for me as a user. 

Hope this helps!

---

### Post by zikki on 2006-06-06
[QUOTE=Human Prototype]...

3. ```
sudo cp cdrecord.prodvd /usr/lib/xcdroast/bin
```
4. Run xcdroast as root and set it all up.
...[/QUOTE]

Thanks for your workaround, but I suppose there should be one more step between 3 and 4:

3.5. set "execute" permissions for cdrecord.prodvd (can be done through gksudo nautilus in /usr/lib/xcdroast/bin)

---

### Post by Haegin on 2006-06-06
[QUOTE=zikki]Thanks for your workaround, but I suppose there should be one more step between 3 and 4:

3.5. set "execute" permissions for cdrecord.prodvd (can be done through gksudo nautilus in /usr/lib/xcdroast/bin)[/QUOTE]
Thanks for that - I have altered my post with the new changes but if you don't want to use XCDRoast then you can just install the latest version of dvd+rw-tools by following the instructions in my earlier post.

---

### Post by RandomGeek on 2006-06-06
Hi,

I've also got an LG HL-DT-ST DVDRAM.  I'm trying to burn a CD image but it keeps failing :-(

This worked easily in Breezy so it's not the hardware (nor the CD image, it's been MD5 checked).

As suggested variously on these forums, I've tried the in-built Nautillus burning program, GnomeBaker and K3B.  All have failed.  I have also tried enabling burn-proof and installing the new DVD+RW tools from [http://packages.debian.org/unstable/utils/dvd+rw-tools](http://packages.debian.org/unstable/utils/dvd+rw-tools).

I'm getting a rather large pile of coasters and increasingly annoyed.  Does anybody have any more ideas?

I have attached a log of a failed burn from K3B.  Any help is much appreciated!

---

### Post by Haegin on 2006-06-07
Well dvd+rw-tools certainly won't help burning a CD but it looks like the error may originate here:
"Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted"
Did you install cdrecord using apt (synaptic/adept) or using some other method? I don't know enough about suid to be able to tell you how to fix this unfortunatly but it's worth looking into.
Also can you burn other stuff onto CD? Just try burning a normal data CD in k3B with no more than 500MB on it just to check it's not a problem with the size of the image.

Also I assume you are burning the image using the burn image tool in k3b rather than just starting a data disk and adding the single ISO file. If not then thats where you are going wrong.

---

### Post by nocturn on 2006-06-07
Just checking in on this issue.

If you find any new information, please do not forget to add it to the bugreport which will cause the devs to look into it.

---

### Post by RandomGeek on 2006-06-07
Hi,

Thanks for the reply.  Yes I was using the K3B burn ISO, I have also tried burning other (and much smaller) data using the 3 different programs but still no joy.

I haven't explicitly installed cdrecord, as far as I know it was installed as part of the Breezy (and presumably updated by Dapper when I upgraded).

I agree that the SUID is a good place to start, so I tried burning the image whilst running GnomeBaker as root - no difference.  Also odd since this worked fine on Breezy (and I never had to change the /etc/sudoers file there).

It's all a bit odd.  I'd do a fresh install but I can't burn the iso! ;)

---

### Post by tsho on 2006-06-07
I have this problem too. With breezy it was all ok. We have problems with any program because all of them use cdrecord, cdrdao or burn cds/dvds and the issue is related to the device.

I have a GSA-4167B. I dump here the cdrecord result just in case someone gets illuminated :) then I think I will have better to file a bug-report...

```
$ sudo cdrecord -dao -v gracetime=2 ubuntu-6.06-desktop-i386.iso
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-23-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4167B'
Revision       : 'DL13'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x000A
Profile: 0x0012
Profile: 0x0011
Profile: 0x0015
Profile: 0x0014
Profile: 0x0013
Profile: 0x001A
Profile: 0x001B
Profile: 0x002B
Profile: 0x0010
Profile: 0x0009
Profile: 0x000A (current)
Profile: 0x0008
Profile: 0x0002
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 13468 kB/s 76x CD 9x DVD
FIFO size      : 4194304 = 4096 KB
Track 01: data   697 MB
Total size:      801 MB (79:23.96) = 357297 sectors
Lout start:      801 MB (79:25/72) = 357297 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 2
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -11077 (97:34/23)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  4 1T speed high: 10
  2T speed low:  2 2T speed high: 10
  power mult factor: 2 6
  recommended erase/write power: 5
  A1 values: 24 2C DC
  A2 values: 14 A4 4A
  A3 values: 04 C4 80
Disk type:    Phase change
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 2552
Starting to write CD/DVD at speed 10 in real SAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Sending CUE sheet...
cdrecord: WARNING: Drive returns wrong startsec (0) using -150
Writing pregap for track 1 at -150
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 FF FF FF 6A 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 90 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 63488
cmd finished after 0.002s timeout 200s
write track pad data: error after 0 bytes
BFree: 1029 K BSize: 1029 K
Starting new track at sector: 0
Track 01:    0 of  697 MB written.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 10 2A 00 00 90 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 63488
cmd finished after 0.002s timeout 200s

write track data: error after 0 bytes
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.
Writing  time:   31.293s
Average write speed 152.5x.
Fixating...
Fixating time:    0.004s
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

```

bye

---

### Post by tsho on 2006-06-09
I've been illuminated. The cause was VMware server. Just disabled it (/etc/init.d/vmware stop) and k3b kept working as usual!

---

### Post by wantilles on 2006-06-10
The problem is probably in k3b.

It always defaults to "Use Burning Group".

Even if the user de-selects it, k3b does not keep the setting as it should.

Also it is a specific Ubuntu Dapper issue, as it does not happen in other distros (Gentoo for instance).

---

### Post by beameup on 2006-06-10
No problems for me. I used Nero and GnomeBaker. Using Ubuntu with GNOME. This machine started with Flight 3, default repositories, and automatic updates to get to 6.06LTS. Machine specs in signature. 

Hope this gets resolved for everyone affected in due time.

---

### Post by henry.tx on 2006-06-11
Just another "me too" here.  Everyhting was fine in Breezy, but now everything I burn on DVD-R media turns out corrupted.  Burned movies are fine at the beginning, but start to show corruption midway through.  Corruption is evident on other hardware and OS, not just on the setup that did the burning.  I have a Toshiba drive: "TOSHIBA ODD-DVD SD-R5272".

I have tried the various suggestions - enable "burnproof" for nautilus, be sure DMA is enabled, install latest "dvd+rw-tools" from Debian unstable - all to no avail.  

One additional observation, though.  After switching to Dapper, I am no loger given the option of burning at 1X, which I have always done in the past because I value reliability above burn speed.  Now the slowest speed that nautilus offers me is 4X.  I even changed the default speed option in gconf to 1 (from 4), but nautilus did not seem to register this change.

Thanks to everyone that has been working on this.  Please someone post here if a solution is found.

Henry

---

### Post by nocturn on 2006-06-12
I burnt the LiveCD and it is working, however the k3b debug log shows this error

```

Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted

```

Burnfree was turned on by default on my system (don't know why), so the disc works.

---

### Post by henry.tx on 2006-06-13
More information.  I don't know if this helps at all, but here it is.  I moved the drive that is burning the coasters after the Dapper upgrade to another machine.  The other machine has a different brand of proccessor (AMD rather than Intel) and different chipsets.  A test burn of a DVD iso resulted in - you guessed it - another coaster.  In the new machine nautilus still did not offer me the chance to burn at 1X.

---

### Post by nocturn on 2006-06-13
The bugreport doesn't seem to have caught anyone's attention yet... :sad:

---

### Post by henry.tx on 2006-06-13
[QUOTE=nocturn]The bugreport doesn't seem to have caught anyone's attention yet... :sad:[/QUOTE]

Indeed...  how can we get attention for this issue?  Is there such a thing as a micro-bounty?  We could all chip in $10 or $15...

I wonder what happened to users "an10ae" and "vyruss"?  They definitely had this same problem, but haven't posted anything in this thread recently.  Gave up?  Resolved?  

I wish I better knew how to poke around under the hood.  If there is no movement in a week or so I may buy a new burner that is known to be working well in Dapper.

---

### Post by nocturn on 2006-06-13
[QUOTE=henry.tx]
I wish I better knew how to poke around under the hood.  If there is no movement in a week or so I may buy a new burner that is known to be working well in Dapper.[/QUOTE]

don't do that.  There are people with many different burners that reported problems, so you have a good chance to spend the money on nothing.

---

### Post by jonrkc on 2006-06-14
Just a note to make myself a member of the No-Burn club.  Funny thing is that I was able to download an ISO on June 11 (three days ago as I write this), under Dapper using K3B, and burn it onto a DVD+RW with no problem.  Today, I was unable to burn a DVD, though I got the "Success!" message at the end.  I was suspicious as there had been no progress bar and it took far too short a time, so I tried reading the DVD+RW and it still had the old files.  So I tried to erase it using K3B and got a "Failed" message and that petulant message from the author of CD-Record that "there are issues" with Linux kernels 2.5... and beyond.  I'd seen that one plenty of times both in Mandriva Linux and Ubuntu.

If it hasn't been fixed for kernel 2.5-x yet it makes me less than optimistic about whatever it is being fixed period.  

Yet sometimes CDRecord works.  Just not, apparently, in Dapper some of the time--as it did work for me (via K3B) three days ago.

I agree that this is a major problem.  It could impact the reputation of Ubuntu, considering how important the burning function is to a lot of users.

Edit: As a footnote, I burned a DVD+RW some days ago and it didn't erase beforehand, but did successfully write the new files in addition to the ones already there: i. e. as though multi-session.  Yet I'm sure I didn't specify multi-session, and I  always thought a DVD+/-RW could not be written multi-session.  I guess that has changed???

Another **Edit:**  Now k3b has decided it's OK to burn DVD's after all.  I followed the same procedures as the time it failed, did nothing significant in between attempts, and have tested it twice now and it's worked OK.  (I also learned that now you can indeed burn CD+RW's without erasing first; it just overwrites whatever old data it needs to.  Result is that some old files remain on the disk, which I'm not too crazy about.)

I would classify this DVD-burning problem as "erratic behavior," in the case of my system.  Still not at all desirable.

In both these successful tests, I did NOT get the "Success!" message which ended up saying the thing didn't work.  Instead, I got a message with no header, and at the end it said it was a failure.  Debugging output asked if I used the same mkisofs...  I don't know.  That's why I use a GUI.

Anyway, I guess in my case if it says "Success!" that means I've got a (reusable) coaster, and if it doesn't, it means all is well.

I'll just have to keep that in mind along with 10,000 other things.

(Edited yet one more time to correct "kernel 5" to "kernel 2.5-x."  I'm really tired; worked on recovering from catastrophic failure 16 hours straight yesterday.)

---

### Post by connellr on 2006-06-15
So, I had been having pretty much the same problem as everyone else.  I first noticed it trying to burn Audio CDs using Serpentine (the default in 6.06 when you insert a blank disk and choose New Audio CD).  This program was saying the burn completed successfully, but when I tried to play the CD only the first few songs were on the disk.  Later I tried with gnomebaker and got an error (similar to what others have posted) after the first few tracks burnt.

I think I have found the solution (with a little help from clues in earlier posts)

In a terminal window I typed:
```
sudo chgrp cdrom /usr/bin/cdrecord
```

Then when I tried burning the CD again, presto ... no more additions to my coaster collection.

Hope this helps.

PS - I changed the group to cdrom - but you can choose any other group that your user is a member of.

---

### Post by jonrkc on 2006-06-15
[QUOTE=connellr]
I think I have found the solution (with a little help from clues in earlier posts)

In a terminal window I typed:
```
sudo chgrp cdrom /usr/bin/cdrecord
```

Then when I tried burning the CD again, presto ... no more additions to my coaster collection.

Hope this helps.

PS - I changed the group to cdrom - but you can choose any other group that your user is a member of.[/QUOTE]
I'm going to try this!  I found out, after thinking (see my post above) that the problem had fixed itself, that the DVD I burned had good files part of the way on it, and the later files were worthless.  So the same problem connellr described.

I'm going to try this fix and I'll report if it also works for me; if so, maybe it will be a solution for at least several others stuck in this predicament.

---

### Post by nocturn on 2006-06-15
[QUOTE=connellr]So, I had been having pretty much the same problem as everyone else.  I first noticed it trying to burn Audio CDs using Serpentine (the default in 6.06 when you insert a blank disk and choose New Audio CD).  This program was saying the burn completed successfully, but when I tried to play the CD only the first few songs were on the disk.  Later I tried with gnomebaker and got an error (similar to what others have posted) after the first few tracks burnt.

I think I have found the solution (with a little help from clues in earlier posts)

In a terminal window I typed:
```
sudo chgrp cdrom /usr/bin/cdrecord
```

Then when I tried burning the CD again, presto ... no more additions to my coaster collection.

Hope this helps.

PS - I changed the group to cdrom - but you can choose any other group that your user is a member of.[/QUOTE]


I will try this when I get the chance.   I'm a little disappointed about the lack of attention that the bugreport got...  If this is it, we can post the fix ourselves.

---

### Post by nocturn on 2006-06-15
The strange thing about the cdrom group fix would be that on Hoary, cdrecord has these permissions:
-rwxr-xr-x  1 root root 133 2005-03-24 10:42 /usr/bin/cdrecord

(Hoary is still on my server)

So, why the regression #-o

---

### Post by nocturn on 2006-06-15
Ok, I may have found something.

Starting from the post that suggested that chgrp cdrom worked for him, I checked the cdrecord package.

Apparently, it has a debconf option to install cdrecord SUID root.

I did this:
dpkg-reconfigure cdrecord
select SUID root
Generating missing device files needed by cdrecord.
root@nirrti:/var/lib/dpkg/info# ls -l `which cdrecord`
-rwsr-xr-- 1 root cdrom 133 2006-04-12 09:32 /usr/bin/cdrecord

Now it is owned by the cdrom group...

---

### Post by henry.tx on 2006-06-15
I tried the
```

$ sudo chgrp cdrom /usr/bin/cdrecord
```
suggested by connellr, but this was even worse.  With my original problem, burning an ISO I got a DVD that workled for the first 1/2 of a movie before the corruption set in.  Now a get a DVD with a 0 bytes file called "hdc" and no movie at all.  I changed the group back to "root" (its group before the change).  nocturn, I will try
```
$ dpkg-reconfigure cdrecord
```
(and select SUID root) when I get home tonight, or is this just going to do the same thing as directly changing the group on cdrecord?

---

### Post by nocturn on 2006-06-15
[QUOTE=henry.tx]
(and select SUID root) when I get home tonight, or is this just going to do the same thing as directly changing the group on cdrecord?[/QUOTE]

It does two things:
- change ghe group ownership
- set the binary SUID root (so people in the cdrom group get to execute it as root)

---

### Post by henry.tx on 2006-06-15
[QUOTE=nocturn]set the binary SUID root (so people in the cdrom group get to execute it as root)[/QUOTE]
Would I then need to do something special to execute as root?  For example, if I start nautilus normaly, then navigate to an ISO, right click it, and select "write to disk", does this miss the point"?  Do I instead need to do something like 
```
$ sudo cdrecord [specify device] [specify iso file]
```
to be sure that I use cdrecord as root?  Or does using it as root happen automatically after it is set "SUID root"?

---

### Post by nocturn on 2006-06-15
[QUOTE=henry.tx]Would I then need to do something special to execute as root?  For example, if I start nautilus normaly, then navigate to an ISO, right click it, and select "write to disk", does this miss the point"?  Do I instead need to do something like 
```
$ sudo cdrecord [specify device] [specify iso file]
```
to be sure that I use cdrecord as root?[/QUOTE]

No, the SUID bit takes care of this.  This only applies to cdrecord though, growisofs and others are not affected by this change.

---

### Post by henry.tx on 2006-06-15
[QUOTE=nocturn]Ok, I may have found something.

Starting from the post that suggested that chgrp cdrom worked for him, I checked the cdrecord package.

Apparently, it has a debconf option to install cdrecord SUID root.

I did this:
dpkg-reconfigure cdrecord
select SUID root
Generating missing device files needed by cdrecord.
root@nirrti:/var/lib/dpkg/info# ls -l `which cdrecord`
-rwsr-xr-- 1 root cdrom 133 2006-04-12 09:32 /usr/bin/cdrecord

Now it is owned by the cdrom group...[/QUOTE]

I just tried this.  After the doing the above, I rebooted just to be sure that the change was effective wherever neccessary, then burned an iso.  The resulting disk refused to be mounted on the machine that did the burning.  On completely different hardware, I was able to mount it.  Like a previous attempt, this disk does not look at all like a video DVD, but intesad has a 0 byte file called "hdc" (which is the burner device - /dev/hdc).  SIgh.  Nice try, though.

---

### Post by henry.tx on 2006-06-15
I notice that there is a newer firmware available for my DVD drive.  I have no Windows partition/installation, however.  Nocturn, I noticed on another forum discussion that you have some experience in this area.  Can I do this somehow using the package "dosemu-freedos", or should I try something like the process outlined by  Karl Hegbloom in the middle of [this page]("http://ubuntuforums.org/showthread.php?t=11962&page=2"), or would you reccomend something completely different?  Thanks again of all of your help here.

---

### Post by jonrkc on 2006-06-15
[QUOTE=henry.tx]I tried the
```

$ sudo chgrp cdrom /usr/bin/cdrecord
```
suggested by connellr, but this was even worse.  With my original problem, burning an ISO I got a DVD that workled for the first 1/2 of a movie before the corruption set in.  Now a get a DVD with a 0 bytes file called "hdc" and no movie at all.  I changed the group back to "root" (its group before the change).  nocturn, I will try
```
$ dpkg-reconfigure cdrecord
```
(and select SUID root) when I get home tonight, or is this just going to do the same thing as directly changing the group on cdrecord?[/QUOTE]
I just got through burning a DVD with exactly the same contents as the one that was corrupted toward the end, and it burned OK as far as I can tell--since there are 3.7 GB of data on it, I'm not going to try comparing all the files, as I probably would have to give up use of my computer for about six hours.  

But anyway, this successful burn was after I did the chgrp thing that connellr suggested, that had apparently worked for connellr.  

Was it just luck, or did that do the trick?  I don't know.  I will have to burn some more DVD's to see if they consistently turn out OK.  

I do know that burning was fine with exactly the same hardware and using k3b as I did here, under Hoary.

---

### Post by viraptor on 2006-06-16
Ok - something old / new. After updating everything lately (I don't know if it happened only because of yesterday's updates), I can't write dvd's at all:
LG's dvdrw, mmc2 driver - end of logs of "dvdrecord dev=/dev/dvdrw speed=2 driveropts=burnfree -dao -vv blablabla.iso":

```
...
dvdrecord: Turning BURN-Free on
Performing OPC...
Sending CUE sheet...
Starting new track at sector: 2249494
Track 01:   0 of 4393 MB written.dvdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 22 53 16 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 63488
cmd finished after 0.001s timeout 200s

write track data: error after 0 bytes
Sense Bytes: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Writing  time:   36.209s
Fixating...
Fixating time:    0.001s
dvdrecord: fifo had 64 puts and 1 gets.
dvdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
```

Nothing in dmesg, disk has something written (fixated probably) and is not writable anymore. Happens every single time.

---

### Post by nocturn on 2006-06-16
[QUOTE=henry.tx]I notice that there is a newer firmware available for my DVD drive.  I have no Windows partition/installation, however.  Nocturn, I noticed on another forum discussion that you have some experience in this area.  Can I do this somehow using the package "dosemu-freedos", or should I try something like the process outlined by  Karl Hegbloom in the middle of [this page]("http://ubuntuforums.org/showthread.php?t=11962&page=2"), or would you reccomend something completely different?  Thanks again of all of your help here.[/QUOTE]

It depends on the brand of drive that you own.  Plextor is one of the few that support a flash utility for Linux.  
If the flash utility for your drive works in DOS, you can always use a freedos bootCD or floppy, I have done this several times for my system BIOS in the past.

I would not recommend flashing from an emulator though (like dosemu).  It may work, but the result is unpredictable and you could wind up with a bad flash (and a dead drive).

If you own a windows XP CD, you can create a windows session on a CD without installing it to the harddrive.  I'm not sure if it works from an install CD or only from a restore CD.  I saw the procedure recommended for my laptop.

---

### Post by nocturn on 2006-06-16
[QUOTE=viraptor]Ok - something old / new. After updating everything lately (I don't know if it happened only because of yesterday's updates), I can't write dvd's at all:
LG's dvdrw, mmc2 driver - end of logs of "dvdrecord dev=/dev/dvdrw speed=2 driveropts=burnfree -dao -vv blablabla.iso":
[/QUOTE]

There was a kernel update yesterday.  I haven't tried burning since....

Good grief, this problem is really escalating and the number of people being hit is  increasing.

I really don't know what we can do to attract attention to the bugreport, as this seems the only sure way to get it fixed.

---

### Post by viraptor on 2006-06-16
[QUOTE=nocturn]There was a kernel update yesterday.  I haven't tried burning since....[/QUOTE]
Yes - as soon as I've seen that, I wanted to check if it fixed anything ;) FAIL!

I don't know if I've posted this already, but if someone has kernel from breezy times, try booting with it in rescue (emergency? whatever) mode and burn dvd. Voila - works for me. Still, booting with normal dapper doesn't work.

---

### Post by nocturn on 2006-06-16
[QUOTE=viraptor]Yes - as soon as I've seen that, I wanted to check if it fixed anything ;) FAIL!

I don't know if I've posted this already, but if someone has kernel from breezy times, try booting with it in rescue (emergency? whatever) mode and burn dvd. Voila - works for me. Still, booting with normal dapper doesn't work.[/QUOTE]

So the kernel seems to be the cause...
Can you append this information to the bugreport viraptor?  I hope someone takes a look at it.

---

### Post by jonrkc on 2006-06-16
[QUOTE=nocturn]So the kernel seems to be the cause...
Can you append this information to the bugreport viraptor?  I hope someone takes a look at it.[/QUOTE]Thanks to all for the information about the kernel update.  Since the last DVD I burned (this afternoon) apparently came out OK, I'm holding off on dist upgrades till further notice.

I could go back to the Hoary kernel, which worked fine, but I'm afraid that might cause other problems...

I do hope some action is taken quickly on the bug report, as CD/DVD burning is an important activity and people are going to be turned away from Ubuntu if it isn't fixed.

---

### Post by viraptor on 2006-06-16
Status after making all updates:
pro = Cdrecord-ProDVD-Clone 2.01b31
dvd = dvdrecord from dvdrtools v0.2.1

kernel:
2.6.15-25-686:
 - pro - fail 
 - dvdr - fail
both with something like
```
CDB:  2A 00 00 22 53 16 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 63488
cmd finished after 0.001s timeout 200s
Sense Bytes: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```

2.6.15-25-686 [recovery]:
 - dvdr - fail as above
 - pro - records, but it's not mountable after that

2.6.12-10-686 [recovery] (from breezy):
 - dvdr - fail as above
 - pro - records, dvd ok (also formats dvd+rw with not problem)

So - where should I raport it now - kernel? dvdrtools? I filled a raport for each of them some time ago (and cdrtools too, as it stopped working lately). Dvdrtools used to work ok on Breezy and produced unmountable (only under this lin box - I can still read them on win box with different dvdreader) just before Dapper official release. Now with new kernel it just fails.

Decoration dvds pile growing... switching to testing dvd+rws, so your experience may vary.

Once again - what raport / logs do developers need EXACTLY? I can log / try anything, but someone has to tell what is needed.

---

### Post by henry.tx on 2006-06-16
Thanks for the info about firmware updating, nocturn.

[SIZE="4"]I think I have some important new info:[/SIZE]  I think that the fundamental problem underlying the bad burns (at least for me) is that the OS is not correctly recognizing the capabilities of my drive, or the proper way to control my drive.

Using the Device Manager, the info for my drive (Toshiba SD R5272) on the advanced tab indicates that my drive is [COLOR="Red"]not[/COLOR] capable of writing to DVD-RW, DVD+R, or DVD+RW ([screenshot1]("http://i78.photobucket.com/albums/j100/subtr4ct/drive.png") , [screenshot2]("http://i78.photobucket.com/albums/j100/subtr4ct/drive-1.png")).  This is all incorrect.  My drive should be able to burn on any of these media (actual specifications for my drive are half way down [this page]("http://www.anandtech.com/printarticle.aspx?i=2039")).

Also, in nautilus, when I right click on a DVD iso and select write to disk, the burn speed choices that are presented to me are 4X, 10X, 12X, 16X, and 32X.  All speeds above 8X are definitely beyond my drive's DVD burn capability.

This all seems too suspicious to not be related.  I think this may be the fundamental problem, while the corrupted burns are just the symptom.

---

### Post by viraptor on 2006-06-16
Not same problem on my side. dvdr, dvdplusr, dvdplusrw set to true here, but still can't write.

---

### Post by taygan on 2006-06-16
I am having the same problem.  Actually, the drive worked at first, then after an update a week or so ago, it showed DVD write speeds going up to 125x!  I looked in device manager, and the actual speeds were fine, but nautilus was converting DVD speeds to CD burner speeds.  Now, the top speed is 52x..  All screwed up.  

Will.

[QUOTE=henry.tx]Thanks for the info about firmware updating, nocturn.

[SIZE="4"]I think I have some important new info:[/SIZE]  I think that the fundamental problem underlying the bad burns (at least for me) is that the OS is not correctly recognizing the capabilities of my drive, or the proper way to control my drive.

Using the Device Manager, the info for my drive (Toshiba SD R5272) on the advanced tab indicates that my drive is [COLOR="Red"]not[/COLOR] capable of writing to DVD-RW, DVD+R, or DVD+RW ([screenshot1]("http://i78.photobucket.com/albums/j100/subtr4ct/drive.png") , [screenshot2]("http://i78.photobucket.com/albums/j100/subtr4ct/drive-1.png")).  This is all incorrect.  My drive should be able to burn on any of these media (actual specifications for my drive are half way down [this page]("http://www.anandtech.com/printarticle.aspx?i=2039")).

Also, in nautilus, when I right click on a DVD iso and select write to disk, the burn speed choices that are presented to me are 4X, 10X, 12X, 16X, and 32X.  All speeds above 8X are definitely beyond my drive's DVD burn capability.

This all seems too suspicious to not be related.  I think this may be the fundamental problem, while the corrupted burns are just the symptom.[/QUOTE]

---

### Post by viraptor on 2006-06-16
Ok - I'm kind of aware that [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37876](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37876) is there, but I think it has general idea wrong - problem with reading dvds (or am I wrond and it is about reading?). I created a dup probably:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50034](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50034)
but pointed it specifically at writing and kernel and I hope for some reply from developers.

PS. If anyone knows a polite and positive way to get some attention to this bug, without posting dups, please contact me. I already feel bad, that I filled bugs on this in dvdrtools, cdrtools and kernel, but noone even told me, what can I provide, to help them resolve it :/ And AFAIK people with this problem can provide any info developers want by recording with max debug level, but is anyone interested in looking through this?

---

### Post by henry.tx on 2006-06-16
[QUOTE=viraptor]Ok - I'm kind of aware that [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37876](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37876) is there, but I think it has general idea wrong - problem with reading dvds (or am I wrond and it is about reading?). I created a dup probably:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50034](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50034)
but pointed it specifically at writing and kernel and I hope for some reply from developers.[/QUOTE]

I agree that [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37876](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/37876) actually looks like it *could* be something distinct from the problems many of are discussing in this thread.  If you created a dupe bug report, I think it would be a dupe of this one: 
[https://launchpad.net/distros/ubuntu/+source/dvdrtools/+bug/46966]("http://https://launchpad.net/distros/ubuntu/+source/dvdrtools/+bug/46966")

Nice work on the testing different kernels.   Sooner or later we have to get down to tthe problem.  There seems to be some kind of long-running cdrecord+kernel interaction problem (google for it) that we may be running into...

---

### Post by kinematic on 2006-06-16
well...i'm running 6.06 fully updated with the latest k7 kernel and i don't have any problems with my nec3540-a dvd writer(if in doubt buy a nec ;)  ).
it seems to be a hardware specific problem since some have problems and others don't.

---

### Post by j_baer on 2006-06-16
I had an LG DVD burner installed during the development cycle and had troubles all of the time. When I installed the RC things got a little better but I decided to replace the drive with a LiteOn.

Just burned a CD with Bonfire and both worked perfectly ...

:D

---

### Post by henry.tx on 2006-06-16
Woot!  After 58 updates for my system today, including the new  2.6.15-25-386 kernel, I burned a DVD that is not corrupted.  Hopefully these updates are helping others here!

---

### Post by IbeeX on 2006-06-18
Hi

I have NEC DVD_RW ND-4550A
and ibee 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 x86_64 GNU/Linux
And I still cant write DVD-rw
I managed to burn CD-rw, but no DVD.

---

### Post by jonrkc on 2006-06-19
[QUOTE=henry.tx]Woot!  After 58 updates for my system today, including the new  2.6.15-25-386 kernel, I burned a DVD that is not corrupted.  Hopefully these updates are helping others here![/QUOTE]I went ahead and updated likewise, and apparently burned two or three OK data CD's and CD-RW's afterward; haven't tried DVD since updating.  

But as of last night I mysteriously all of a sudden couldn't burn ANYTHING.  I tried gnomebaker, Nautilus's cd-burner, k3b (my usual), and even some CD-burning utility on a Damn Small Linux installation I also have on another hard drive.  

In all cases, there appeared to be activity, but nothing was actually happening--nothing at all.  According to gkrellm, about one percent CPU usage; no CD activity (despite the light coming on); no hard-drive activity.  It's as though the burning programs had been fooled into thinking they were actually doing something.  It's almost like being back with that operating system 95% of the world uses....  :(

---

### Post by Drifter on 2006-06-21
Could this be the reason I can't backup and restore in dapper with cdrw's I use quicken with crossover office and can't get it to back up to cdwriter.

---

### Post by Haegin on 2006-06-22
Almost certainly not. Ubuntu uses two different programs for CD and DVD writing.
The first is cdrecord which is only for CDs.
The second is growisofs which is used for DVDs.
What errors do you get when you try and burn a disc? Also what are you using to burn the disc? I would recommend trying something like gnomebaker, graveman or bonfire on Gnome or k3b on KDE.

---

### Post by Daniel Ngu on 2006-07-03
Hi,

Has anyone found out the cause or resolution to this one. I'm running 6.06 but all my dvd came out as coasters. I'm using growisofs. I think I've at least narrow it down to growiosfs. Tried different speed as well but no difference. The only clue I found is that I read that growisofs does not like the blank media to be mounted for burrning but I've checked that it is not.

Thanks.

Daniel

---

### Post by jonrkc on 2006-07-03
[QUOTE=Daniel Ngu]Hi,

Has anyone found out the cause or resolution to this one. I'm running 6.06 but all my dvd came out as coasters. I'm using growisofs. I think I've at least narrow it down to growiosfs. Tried different speed as well but no difference. The only clue I found is that I read that growisofs does not like the blank media to be mounted for burrning but I've checked that it is not.

Thanks.

Daniel[/QUOTE]
I don't know why, but my K3B started working normally again, and creates CD's, CD-RW's, and DVD+RW's just fine now.  I haven't tested DVD+.

I didn't do anything that I can think of that should have changed a thing.

It's truly puzzling.

---

### Post by Haegin on 2006-07-05
Daniel,

What have you tried? Have you updated to the latest version of cd+rw-tools from the debian website? What works (do CDs etc)? Is it only DVDs that don't work.

There seem to be many problems with similar symptons all in this thread. I need more information.

---

### Post by viraptor on 2006-07-24
Please check dvd writing now :)
It started working for me. 100% written correctly and readable. I don't know which update did it, cause I haven't tried writing for a long time, but after 2 kernel updates I thought I'll try... And success!
Checked with Gnomebaker. Burned 9 dvds yesterday and all of them are ok.

---

### Post by songo on 2006-07-24
hi there...
just to report what happened to me when trying to burn a dvd-rw

graveman throws an 'input/output error'.
k3b actually burns it but there's no way to mount it after it's burned.(i read something about not been able to close the session?)
gnomebaker blocks. i had to kill him. didn't tried it anymore yet since k3b is partially working.

> I don't know which update did it, cause I haven't tried writing for a long time, but after 2 kernel updates I thought I'll try.
so, which kernel do you have now viraptor? i still with 2.6.12

---

### Post by viraptor on 2006-07-25
I'm using dapper, fully updated, 2.6.15-26-686.
Got exactly the same problems before and wrote about them many times. Now it works.

---

### Post by songo on 2006-07-26
hmm.. good for you!
but i'm [convinced]("http://www.fedoraforum.org/forum/archive/index.php/t-94820.html") if I could ugpgrade the dvd+rw-tools to 6.1 (maybe with an upgrade to K3b also) it would solve the problem.
I've tried. I downloaded dvd+rw-tools_6.1.deb dpkg -i it and screwed up. dependencies issues.

since apt-get still with the 5.1 version, how can I install dvd+rw-tools without messing up the dependencies? 

tanx

---

### Post by dweebs0r on 2006-08-29
Anything new on this?  I am still unable to burn DVDs.

This is the first install of Linux I have ever used that everything just seemed to work like it was supposed to -- until I tried to burn DVD's.

-

---

### Post by tekrei on 2006-09-01
I was able to burn dvd's one week before, and now i couldnt burn (tried graveman, k3b). Looking in k3b devices section my dvd burner's max speed is 0. I hate losing dvds. And afraid burning.

---

### Post by hanzomon4 on 2006-09-01
mkisofs -ddvd-video gives this error ```
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
```

---

### Post by Peturrr on 2006-09-03
I also can't burn DVD's. 

Burning data on an empty DVD-RW gives me:
```

/dev/hdb: "Current Write Speed" is 2.5x1385KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=64h/ACQ=00h]: Input/output error
:-( attempt to re-run with -dvd-compat -dvd-compat to engage DAO or apply full blanking procedure
:-( write failed: Input/output error

``` 
No messages in kernel logs, dmesg etc. 
DMA is enabled
K3B and gnomebaker => same issues.

---

### Post by Peturrr on 2006-09-03
[B]A Solution!
[/B]Gnomebaker  and K3B work for me now, but only while using DiskAtOnce. 

The solution was: ```
Make sure your DVD burner is MASTER not SLAVE.
``` 
I did shutdown my PC, changed the jumper on the drive so it would be master instead of slave, started the PC and suddenly Gnomebaker didn't gave me any errors and I succesfully burned my dvd data disc!!

---

### Post by kairu0 on 2006-09-08
Problems here burning dvds (DVD-R) in both k3b and gnomebaker. Dmesg simply says:

```
[17179603.980000] cdrom: open failed.
```

Output of hdparm for /dev/cdrom is:

```
/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

I hope someone has mad some progress with this. Anyone?

---

### Post by kairu0 on 2006-09-10
3 good DVDs in a row using IO_support=1 and unmaskirq=1:

hdparm /dev/cdrom:
```
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

---

### Post by abu_nawas on 2006-10-06
i can burn the dvd, but it slow like hell and the system keep prompt me to choose disc type

---

### Post by viraptor on 2007-02-13
Now dvd & cd (exactly the same problems) burning issue.

Hey - back to old topics. It stopped working soon after ;)
[https://launchpad.net/ubuntu/+source/dvdrtools/+bug/46966](https://launchpad.net/ubuntu/+source/dvdrtools/+bug/46966)
Didn't think it's connected, but both came back in the same time:
[https://launchpad.net/ubuntu/+source/cdrtools/+bug/48504](https://launchpad.net/ubuntu/+source/cdrtools/+bug/48504)
So of course kernel bug was updated also:
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/50034](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/50034)

Ok... back to basics :)
Any news on the issue?
Still doesn't work with edgy, or edgy with wodim from feisty.
Welcome to 2007 episode of burning problems.

---

### Post by ShaqArif on 2007-06-06
I've been having CD writing problems ever since I switched to Linux :-(

I've tried every solution on this forum, I've tried every different CD writing program including CLI cdrecord, wodim, brasero, xcdroast, gnomebaker...

This is the error I get in all these cases, for example running 

sudo wodim dev=ATAPI:/dev/hdc -speed=16 -data -v -dummy ~/Downloads/Packages/ubuntu-7.04-desktop-i386.iso

I've tried lower speeds, non-dummy (the -dummy produces less coasters, but gives the same errors)

Error I get:
 
```
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
Sense flags: Blk 0 (not valid) 

```

My /etc/hdparms.conf contains this:

```
#/dev/hdc {
#       dma = on                   
#       interrupt_unmask = on
#       io32_support = 0
#}
```

My /etc/fstab contains:

```
/dev/hdc /media/cdrom0 auto user,noauto 0 0

```

I did manage to write one CD successfully using the above wodim command, but I have a group of colleagues who all want to try out Ubuntu and it doesn't fill them with confidence when I tell them I can't figure out how to burn a CD image, so any help would most gratefully be accepted!!

---

### Post by ShaqArif on 2007-06-15
bump:

Still haven't got past this issue, so I've installed Windows on a separate partition and am using that for all my disc burning...

If anybody has any suggestions, I would love to hear from you, as I really could do with getting rid of WinXP...

---

### Post by Sunflower1970 on 2007-06-15
Did a bit of googling on this. Seems there are quite a few people that have ha the problem in the past. Here's one example [http://209.85.165.104/search?q=cache:Vwi8UJiwYZEJ:www.linuxquestions.org/questions/showthread.php%3Ft%3D79353+%22Sense+Key:+0x4+Hardware+Error,+Segment+0%22&hl=en&ct=clnk&cd=4&gl=us&client=firefox-a](http://209.85.165.104/search?q=cache:Vwi8UJiwYZEJ:www.linuxquestions.org/questions/showthread.php%3Ft%3D79353+%22Sense+Key:+0x4+Hardware+Error,+Segment+0%22&hl=en&ct=clnk&cd=4&gl=us&client=firefox-a)

Some info that might help. Scroll down to the very end.

[http://readlist.com/lists/vger.kernel.org/linux-kernel/4/22194.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/4/22194.html)

Some of the stuff I read said it could be a bug in the kernel, could be the drivers, could be the medium being burned (CD-RW's) Maybe the speed...

I know this isn't a great answer, but maybe it'll help point where to go to get one..?

Have you tried any other distros? Maybe another one has better support...

---

### Post by ShaqArif on 2007-06-22
Hi Sunflower, thanks for the response!

I don't think the problem is hardware, either CD Writer or media, because it works fine in Windows.  Also I'vetried burning at 2x speed, and I still get the same error.  
I have tried Mandriva (latest version), but I got exactly the same error. :(

I'll try the MDMA think mentioned in that second link and we'll see how it goes.

personally, I think it's a kernel issue, not that I have any reason for thinking that...

cheers!

Shaq

---

### Post by tdelov on 2007-06-30
Hi All,
I think I have the same issue with burning DVD's in Ubuntu 7. (wokred fine in ubuntu 6)
I'm wondering if there has been any work arounds or fixes for this DVD problem?

---

### Post by kelvin spratt on 2007-06-30
i've never had a problem burning anything with any flavour of Ubuntu

---

### Post by LeeJunFan on 2007-07-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/dvdrtools/+bug/46966](https://bugs.launchpad.net/ubuntu/+source/dvdrtools/+bug/46966) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I tried today with gutsy, same problem.

I can't burn (at least) video DVD's:

 - whether they be already made iso's or file structures (on the fly).
 - with ubuntu or my vanilla 2.6.19.7 kernel (which I normally use because of ACPI problems with newer kernels)
 - normal or slowest speeds
 - using older groisofs v6.1 (I think this is dapper's version)
 - I get no errors
 - I can burn the same image 5 times and one of them might work in my DVD player, but they never read in the PC.

hdparm -i /dev/hdc

shows that I have a Model=TSSTcorpCD/DVDW TS-L532A, FwRev=TI94, SerialNo=554H209165

Which I noticed is the same model in the bug report [https://bugs.launchpad.net/ubuntu/+source/dvdrtools/+bug/46966]("https://bugs.launchpad.net/ubuntu/+source/dvdrtools/+bug/46966") by myself and at least one other person experiencing this problem.

I'll try dropping back to even older versions of dvd+rw-tools.

---

### Post by LeeJunFan on 2007-07-05
No deal, growisofs sucks, plain and simple, I have to use windows to burn DVD's.

---

### Post by cdysthe on 2007-07-07
I've had it. I'm now posting from PCLinuxOS where I can burn just fine. To me an OS is a tool, and when I can't do what I need to have done I have to find a solution. In this case it was Windows or another Linux distro. I have been without burning capabilities for too long. 

I'm afraid this burning issue (pun intended) is going to harm Ubuntu both among new and experienced users. Sad!

I really like Ubuntu, the OS, the community and the whole concept, but when I spend all my time getting my burner to work I just can't deal with it for weeks and even months. Sorry.

Gotta go. I have 268 dvd's to burn! :)

//C

---

### Post by BCtom on 2007-07-07
Yes, I too am in the same situation as I am about to do the largest network file transfer of my life onto my roommate's Windows PC: just to burn my home movies! This is a humbling moment for me as my roommate's killing himself laughing at me because I can not, for the life of me, burn a DVD on Ubuntu. I have tried for the last two days to get this DVD burnt, but to no avail. It worked fine before the last Kernel upgrade (16), but even switching back to (15) does not make a difference. 

I have tried K3d, and CD/DVD Creator, and even created iso files and tried to burn those, but nothing. I have a stack of coasters sitting on my desk and my hard drive is getting full. 

Please anyone----why all of a sudden does DVD burning not work in Ubuntu? Is it copy write issue? Is the Kernel broken? Is there a fix for this problem in Ubuntu?

Sorry if I sound abrasive---but I need my DVD Burner. ](*,)

---

### Post by BCtom on 2007-07-07
OK....?????  Disregard my previous post. In a last minute attempted I read another thread that said try GnomeBaker as a DVD Burning program. Apparently is does work, it does something different in the burnung process, I don't what--I'm still a newbie. I installed it about half an hour ago and I just burnt a Data DVD with it, and it plays back!

I sure hope this helps you all out. It's better than using a Windows PC: YUCK!!!!!


I'm happy once again. Ubuntu Friend!

---

### Post by minoas on 2007-07-14
Same Here.After 2 months of normal Burning and without touching the installation packages I again am facing too slow dvd burns with all aps.My DMA is on on both devices modules are correctly loaded and I got no way of even searching for a fix...Its really annoying burning a DVD at 30mins with a 18x drive

---

### Post by aceshigh83 on 2007-07-31
deleting my ubuntu installation now as i am unable to write dvd or cds at all, it worked flawless in windows. None guides on this forum helped me. Shamy really since i liked ubuntu

---

### Post by bogolisk on 2007-07-31
[http://ubuntuforums.org/showthread.php?p=3110155#post3110155](http://ubuntuforums.org/showthread.php?p=3110155#post3110155)

---

### Post by Haegin on 2007-07-31
[quote=aceshigh82]deleting my ubuntu installation now as i am unable to write dvd or cds at all, it worked flawless in windows. None guides on this forum helped me. Shamy really since i liked ubuntu[/quote]

Sorry to hear you are going. Do check back when Gutsy comes out in October and if you stay subscribed to this thread then you may find a solution that is worth trying. The upgrade from dapper to edgy fixed it for me and it has been fine since then so there is hope yet.

---

### Post by jackmc on 2007-08-02
If you have the input/output error that has plagued me for days, have a look at my thread:

[http://ubuntuforums.org/showthread.php?p=3119859#post3119859](http://ubuntuforums.org/showthread.php?p=3119859#post3119859)

I found a solution that works fine, as long as you use k3b - maybe others with a lot of config options too.

---

### Post by ShaqArif on 2007-11-08
> **Human Prototype said:**
> Sorry to hear you are going. Do check back when Gutsy comes out in October and if you stay subscribed to this thread then you may find a solution that is worth trying. The upgrade from dapper to edgy fixed it for me and it has been fine since then so there is hope yet.

Another one going to PCLinuxOS... :(

Upgraded to Gutsy, and tried burning a disk, still get the same error.  A shame, because I really liked Ubuntu, I had my desktop set up just the way I like it, with Compiz Fusion, Conky, and all my other favourite apps.

I don't think I ran at the first sign of trouble, I have a whole spindle of coasters to attest to that, and several posts on this forum that show I did try...

I will keep an eye out on this forum just in case this issue ever gets fixed (Hardy Heron?)

---

### Post by mmcmonster on 2007-11-08
Did you really upgrade or a clean installation?

If you have a separate partition for /home, a clean installation is always better.  It also gives you time to clean all the cruft applications. :-)

P.S.  I had DVD and CD burn issues just a week or two before Gutsy came out.  I attribute it to library conflicts, since I had four or five burning applications installed by then.  A clean installation and using Brasero perfectly now. :-)

---

### Post by zenrox on 2007-11-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/157803](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/157803) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				i have done a clean install
tried stoping hal 
done the ignore the speed
nothen works
this is a major issue
and ubuntu burnt fine in feisty 
what changed between fiesty and gutsy

---

### Post by Ubukanuba on 2007-12-01
I too am having problems burning anything.  I cant even get the permissions for my drive to switch from read only to read and write....it always says permission denied.  How am I supposed to burn if it thinks its not allowed to?

---

### Post by riggits on 2007-12-01
Will moving to PCLinuxOS help to burn discs with files > 4GB??? I'm at my wits' end right now with this issue. The only solution I've got is to take my EXT3 hard drives and plug into my Windows XP machine with the ext2fs driver installed. It's a horrible workaround.
Any help, please post here: [http://ubuntuforums.org/showthread.php?p=3852290]("http://ubuntuforums.org/showthread.php?p=3852290#post3852290")

---

### Post by tekniche on 2007-12-18
Same issue here. Been trying to burn a few iso's just by right clicking and going to "write to disc" and am getting an error that says : Error: There was an error writing to disk. Glad it gave me all that information. But the entry in the sys log says that it is attempting to access beyond end of device on hdc which is my dvd burning drive. Anyone have any ideas? Thanks.

---

### Post by frychiko on 2007-12-22
Ditto that.

Getting errors trying to burn ISO's on my Gutsy Laptop and Gutsy desktop. Works fine burning in Windows though.

---

### Post by sujoy on 2007-12-22
strange enough I am using Gutsy since october 20 and have never had any burning issues......... infact my nero in windows f**ked up at times but K3B works fine.... and has been pretty reliable........... I am using Ubuntu 7.10 and the only KDE app I am using is K3B.............. 

one thing is that I only burnt data discs (around 20) , without any error..........didn't try other burning options

---

### Post by sanddgroper on 2008-01-23
I would like to add some of the things I have found about dvd burning/playing.
The easy answer is find a version of Ubuntu that dvd burning/playing works on
and stick with it.
For other information read on.
I have a amd 2000 system with 512Mb of ram a cd/dvd reader(broken)and a cd/dvd rw
and a removable hard drive bay.I have 3 versions of Ubuntu installed on 6 HDD's.Those
versions are 6.06lts,7.04 and 7.10.All the CDs/DVDs I have burnt have been burnt using
either NERO on windows 98 or K3b on linux.
All the CDs that I have burned work fine on all three versions with the desktop icon
appearing and the file browser displaying the CDs contents.
Also DVDs I have that came off the Linux Format magazine work fine to.

THE FUN STARTS WHEN I TRY TO READ DVDs I HAVE BURNED MYSELF.

6.06lts
This version works pretty much ok with just the odd DVD not opening on the desktop.
But by and large I can get most of the DVDs I have burned to open normally.

7.04
I have no trouble burning DVDs with K3b on this version but when I go to play them
I get an unable to mount volume warning and nothing.But I can eject the DVD by pushing
the button on the DVD rw.

7.10
Things get a little funny here.
When I boot the system and check under Places >Computer I see both of my CD/DVD
drives and the filesystem.But if I put a dvd that I have burned in the drive the CD/DVD rw
vanishes leaving me with just the the CD/DVD reader and the filesystem icons.After the
drive vanishes the drive actually keeps going then after about a minute the file browser
comes up with the contents of the drive and you can copy information from the drive like
normal even though the drive icon is nolonger visable in Places > Computer.Also no icon
appears on the desktop and all I need to do is push the button on the drive to eject the disk just like Windows.
Now another strange thing. The CD/DVD rw that vanished stays that way until I put a
Linux Format DVD in the drive and then it reappears in Places >Computer and the icon for the DVD appears on the desk top.Go figure I guess.

So on the same computer hardware I get three different results depending on the version I am using.
It would appear that reading your own home burnt DVDs is a bit of a hit and miss affair.
Maybe some one can make some sense of this.

Cheers
Sandy

---

### Post by izi on 2008-04-12
I've been digging around this for ages now and may have found a solution:

For me as well - functionality has been going down with versions - from a good experience with 6.06, to problems with 7.04 and 7.10, and with 8.04 beta - a complete dud.
I can burn all I want but cant read it later and with 8.04 I don't even get 'dmesg' errors (but on my roommate's windows everything works fine :confused:). In 7.04 / 7.10, where I usually had problems mounting right after burning a DVD with >4GB of data, I used to solve the problem by installing the package 'udftools' and running:

```

> eject
> sudo /etc/init.d/udftools restart

```
which usually solved the problem.

Sadly in 8.04 this stopped working. So, I did some digging in LKML and found somewhere that if you have a SATA (as in Hard drive) and PATA (as in DVD-RW) working together there's a bug with the internal kernel mechanism that handles this (sorry but I lost the reference). For some reason this was never solved or at least resurfaced somehow. I think I may have found a solution, but I'm still trying this new setup and I'd love your comments:
NOTE: this method involves messing around with kernel parameters. This can be dangerous ! make sure you backup everything before you start and that you have a liveCD at hand in case you mess things up. 

OK, now that you're scared lets started: the idea is to circumvent the kernel with a mechanism called 'libata'.

Open the file '/boot/grub/menu.lst'. You should find at the end of the file three groups of lines that start with 
```

title        Ubuntu hardy/gutsy .... 
kernel   /boot/vmlinuz-2....
initrd     /boot/initrd...

```
Usually the first one is the default kernel setup you boot into.  You can verify it by looking at the line at the beginning of the file: 
```
default        0
```
Now carefully, add to the end of line that starts with 'kernel' the parameters:
```
combined_mode=libata atapi_enabled=1
```
Now save the file and run:
```
sudo update-grub
```

If you don't get any errors try rebooting and see if it works for you. I'm still testing this so I would appreciate your comments

---

### Post by zenrox on 2008-04-13
ok i tried the above method in hardy growisofs said it burnt the disk
IT dint
i am trying to burn on the the disk agine  so far no luck
 intel i845gv mobo
liteon dvd +/- rw drive 
all my hdds act like like sata drives
same with my dvd burnner 
all the drives are ata100 and the dvd rw = ata66 
so wtf

---

### Post by terrifickid on 2008-05-26
Just chiming in,

I am having this exact same problem!

I gotta backup this data! I have too much! Very sad.

-TK

---

### Post by fjherna on 2008-05-26
Hi All,

I recently notice that I had problems with Data DVD-R burnt at my Ubuntu 6.06 LTS.

I have not problem at all with any other media (DVD-RW, original DVDs, DVD burnt on other OS)
Data DVD burnt in an DVD-RW is not a problem at all.

My Ubuntu 6.06 LTS is running kernel 2.6.15-k7 on an AMD CPU Athlon 64 x2
My DVD-RW Drive is a SONY AW-G170A
My growisofs is version 7.0.1
My K3b is version 0.12.17
I have burnt DVD-R with gnomeBaker (just in case) with the same results.

Basically the problem is:

    I can burn the DVD-R but I am not able to read/mount them afterwards.

All those DVD-Rs can be read on "any" of all the other Systems and OS I have tested: Windows, Libranet, Ubuntu 6.06 LTS,
Ubuntu 5.10, etc... So in a different hardware the DVD-Rs can be read/mount without problem.
I have in the same system an Ubuntu 5.10 but that is not able to read/mount the DVD-Rs either.
I have installed also a KNOPPIX with kernel 2.6.20.

I have been searching through the net for an answer but I have not found a satisfactory one yet. There are some threads opened at Ubuntu forum and here but I can not find a clear answer that address the problem.

Today I have discover something interesting that maybe can give some light to the experts:
- I have installed VirtualBox and a Windows XP in that system. I was booting that WinXP (guest) over my
Ubuntu 6.06 LTS (host). After the WinXP was booted I insert any of the "failed" DVD-Rs in my DVD drive; then the DVD-R was automatically mounted by Ubuntu 6.06 LTS at the same time as a Nautilus window was opened showing me all the content of the DVD-R; parallel to this, WinXP over VirtualBox opened an explorer window with the content of the DVD-R.

I check /etc/mtab and it showed me that the DVD-R was mounted like an "iso9660" drive.

If I try to mount the DVD-R at Ubuntu 6.06 (sudo) with the command line:
sudo mount -t iso9660 /dev/hdc /media/dvd
I get an error message:  
-----------------[snip]----------------------------------------
localhost kernel: [17228212.812000] attempt to access beyond end of device
localhost kernel: [17228212.812000] hdc: rw=0, want=68, limit=4
localhost kernel: [17228212.812000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
--------------------[snip]-----------------------------------

This is really amazing mainly because I thought that the problem was the DVD drive but now I am not sure at all.

Any suggestion ?

Best regards,

---

### Post by zenrox on 2008-05-30
> **fjherna said:**
> Hi All,

I recently notice that I had problems with Data DVD-R burnt at my Ubuntu 6.06 LTS.

I have not problem at all with any other media (DVD-RW, original DVDs, DVD burnt on other OS)
Data DVD burnt in an DVD-RW is not a problem at all.

My Ubuntu 6.06 LTS is running kernel 2.6.15-k7 on an AMD CPU Athlon 64 x2
My DVD-RW Drive is a SONY AW-G170A
My growisofs is version 7.0.1
My K3b is version 0.12.17
I have burnt DVD-R with gnomeBaker (just in case) with the same results.

Basically the problem is:

    I can burn the DVD-R but I am not able to read/mount them afterwards.

All those DVD-Rs can be read on "any" of all the other Systems and OS I have tested: Windows, Libranet, Ubuntu 6.06 LTS,
Ubuntu 5.10, etc... So in a different hardware the DVD-Rs can be read/mount without problem.
I have in the same system an Ubuntu 5.10 but that is not able to read/mount the DVD-Rs either.
I have installed also a KNOPPIX with kernel 2.6.20.

I have been searching through the net for an answer but I have not found a satisfactory one yet. There are some threads opened at Ubuntu forum and here but I can not find a clear answer that address the problem.

Today I have discover something interesting that maybe can give some light to the experts:
- I have installed VirtualBox and a Windows XP in that system. I was booting that WinXP (guest) over my
Ubuntu 6.06 LTS (host). After the WinXP was booted I insert any of the "failed" DVD-Rs in my DVD drive; then the DVD-R was automatically mounted by Ubuntu 6.06 LTS at the same time as a Nautilus window was opened showing me all the content of the DVD-R; parallel to this, WinXP over VirtualBox opened an explorer window with the content of the DVD-R.

I check /etc/mtab and it showed me that the DVD-R was mounted like an "iso9660" drive.

If I try to mount the DVD-R at Ubuntu 6.06 (sudo) with the command line:
sudo mount -t iso9660 /dev/hdc /media/dvd
I get an error message:  
-----------------[snip]----------------------------------------
localhost kernel: [17228212.812000] attempt to access beyond end of device
localhost kernel: [17228212.812000] hdc: rw=0, want=68, limit=4
localhost kernel: [17228212.812000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
--------------------[snip]-----------------------------------

This is really amazing mainly because I thought that the problem was the DVD drive but now I am not sure at all.

Any suggestion ?

Best regards,

exactaly the same thang
execpt the drive mine is a liteon 
and cd burrning capability is also out now
and the drive is called sr0 not hdc
wtf is going on with the kernel libata,ata_piix arethe 2 modules in the kernel that i have focied in on that are the probs at least in ubuntu
and posabily the patches that ubuntu uses on the kernel
savue the probs dont exist on other linux flavors with the same kernel revisions
so wtf is going on!!!!!!!

---

### Post by slumbergod on 2008-06-10
just went to burn my first data dvd since recent upgrades to Hardy. 

I can burn fine with cli but I just cannot mount it! Hardy has been such a dog for me when it comes to burning. I settled on the cli but with each update it seems to break again.

---

