---
title: "Xorg consumes all CPU power after long idle time"
date: 2006-03-07
forum: Desktop Environments
---

### Post by Crenshinibon on 2006-03-07
Hi everyone,

I have a severe problem with Xorg. After an idle time around a day or so Xorg consumes all available cpu power (around 90%). I googled this topic but didn't find a solution.

My system:
P4 2,4 GHz
1,5 GB DDR 400
NVidia Geforce 4 ti 4200

Ubuntu 5.10 Breezy

Any hints are wellcome.

Greetz Crenshinibon

---

### Post by darknightuk on 2006-03-07
what kernel version are you using?

---

### Post by Crenshinibon on 2006-03-07
My Kernel version is:
2.6.12-10-386

---

### Post by Crenshinibon on 2006-03-08
Did anyone experience similar problems with Xorg. I can not believe I'am the only one.

Any hints are welcome
Greetz Crenshinibon

---

### Post by Jason_25 on 2006-03-08
I'll give a general troubleshooting list.

1.check for latest updates
2.check for hardware trouble.  memtest,prime, etc...
3.change video driver to vesa or something different
4.change kernel, maybe to the 686 one
5.review any changes recently made

---

### Post by NemoTheLobster on 2006-10-11
I've seen the same problem for a long time on hoary, breezy, dapper, and now edgy on two different laptops.  It seems related to when the screen blanks.  I don't run a fancy screensaver, but gnome-screensaver is running to lock the screen.  I believe I saw the same thing running xscreensaver.  Things will run fine then  one time after blanking Xorg will take 99% cpu and everything runs sluggishly.  It happens when a lot of things are running or when nothing is running but my basic desktop.

How can I tell what Xorg is actually doing?  Is there a way to turn on extra logging or something?  I have checked the Xorg.0.log, I just see this around the time it started:
```
SetGrabKeysState - disabled
(**) RADEON(0): RADEONSaveScreen(2)
(**) RADEON(0): RADEONSaveScreen(0)
(**) RADEON(0): RADEONDisplayPowerManagementSet(1,0x0)
(**) RADEON(0): RADEONSaveScreen(2)
(**) RADEON(0): RADEONDisplayPowerManagementSet(2,0x0)
(**) RADEON(0): RADEONSaveScreen(2)
(**) RADEON(0): RADEONDisplayPowerManagementSet(3,0x0)
(**) RADEON(0): RADEONSaveScreen(1)
(**) RADEON(0): RADEONDisplayPowerManagementSet(0,0x0)
SetGrabKeysState - enabled
```
Obviously there's no time stamps so I can't be positive.  Any other suggestions of what to check?

---

### Post by antisho on 2006-11-01
I have a similar problem. After I upgraded to Edgy Xorg started sitting in the processes list sucking up CPU: up to 70 percent at times, and not just after a while or after screen blanks. It never did this in Dapper. My friend suggested that it might be problems with ATI; there is no direct rendering in glxinfo. Reinstalling xserver-xorg-video-ati got me only
```
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::SpacerItem', <> line 1 during global destruction.
```
and successful install otherwise. Finally, said friend complained about Edgy enabling composite by default, and suggested adding
```
Section "Extensions"
Option "Composite" "false"
EndSection
```
to xorg.conf, but nothing was accomplished.

---

### Post by mvarga on 2006-11-15
I have the same problem. If I leave the machine alone for several minutes, the CPU usage goes to 100%. I'm using KDE and kernel 2.6.17-10.

---

### Post by Bartender on 2006-11-16
Glad I caught this thread.  My old PIII usually shows around 7 to 10% CPU usage when idling.  The other day I left it on all day.  CPU usage was around 35% late in the afternoon.

---

### Post by servio on 2006-12-16
Similar problem:  Dapper (6.06) (yep, on a laptop)

Oddly, 
[LIST=1]
[*]Xorg consumed 95%+ of cpu *only after* updating via prompt by Update Manager today (Dec 16)
[*]Problem seemed to stop just after "waking" the screen from the screensaver that had just kicked in
[/LIST]

A couple hours after the "reverse affect" and Xorg is behaving.
Odd?

Update Dec 18:
Xorg spikes %CPU (95%+/-) when visiting webmd.com.  No other web pages (so far) have same result.  Not sure if this web page was loaded previously when cpu spiked (see above).

---

### Post by Tiede on 2007-01-09
Having similar problems here on an acer aspire 3003 WLCi laptop, running the edgy eft, with all the updates, bells and whistles. Xorg takes up 30-90% of CPU power when the screen goes blank. I previously thought it was a GL-Screensaver issue, since my laptop's graphics card is known for not being quite friendly with 3D ( it's from Sis, and it's a 760 ) but I have put the option to blank screen so I can monitor the behavior with a less cpu-intensive environment, and it still happens.
As soon as I return to normal use - i.e unblank the screen through either keypress or mouse event, xorg throtles down to around 17% usage, than back to normal.
Anyone knows if this has been reported on launchpad?
Any ideas what logs the devs might need to help on this one?

---

### Post by Tiede on 2007-01-10
Writing to report that if I disable the screensaver, and the computer is inactive, then beagled takes an exponentially increasing amount of my CPU power, until it finally reaches 100%... This is really annoying!

---

### Post by ge5239 on 2007-02-23
wonder if this is the same one i got, i only get it in kde though. thought it was a bad update from 6.06->6.10, but same problem after fresh install with kubuntu 6.10. 
love kde, and would hate leaving it just cause xorg keeps using all my cpu. 

this isnt after idle'ing though, im usually just posting on forums when all of a sudden my comp gets slower and slower. 
as i write this, xorg is using up ~50% cpu, on my amd3800+.

---

