---
title: "Dell &quot;Studio XPS 1640&quot;: Own or operate one ? Join us"
date: 2011-03-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by astrobob.tk on 2011-03-12
Hello Dell(ers),

I started this thread for me & all the Dellers out there that own &/or operate Ubuntu on a Studio XPS 1640.

If you are one, please join the thread, tell us about ur configuration (hardware & software) & any problems that u have (been)/ are facing. Maybe we can help each other ;)


I myself have the following configuration:

Hardware: 15.6" screen, 4 GB RAM, 500 GB HDD, Core 2 Duo @ 2.53 GHz, 6 cell battery
[i bought this device lst August after my Inspiron 8600's screen hinges broke; i still have it around but still haven't fixed it yet.]

> Software: Win 7 (factory set, rarely used), Ubuntu 10.04 (gnome+fluxbox). I've also tried live version of Lubuntu & Knoppix 6.5

> Problems: When i first got the laptop, I faced the problem of connecting to a wifi (on Ubuntu of course), but soon I figured out that I only had to activate the driver from the "Hardware dirvers".

> Current semi-problems:

1)When brought back from Suspend or Hibernate mode, CPU alternate @ 100% (i mean, one cpu is always at 100% & the percentage flips between the 2 cpu's)

2) When system stars up, the bluetooth light turns on by it self & sometimes the wifi doesn't turn on when I try to turn it on unless I reboot.

3) ever since i bought it the sound seems to be higher on the right speaker that on the left one :S


what about you ? :D

---

### Post by Sophont on 2011-04-09
My specs are in the signature.

I had to stay at Lucid because testing 10.10 with live cd didn't boot.

Otherwise hardly had any problems.

My wifi works with kernel driver:
Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh]

I kept windows on a reduced partition for games - looking forward to delete that when the open AMD drivers 3D acceleration for 4670 has matured. The proprietary driver mostly works - but not really good enough for games and no better than the free driver for 2D.
On my prior Inspiron 9400 with NVidia card games (EVE Online, DDO, Left 4 Dead) worked fine via wine for years (with prioprietary nvidia drivers).

Similar problems with hibernation. It kinda works but is glacially slow so I never bother and shutdown instead. Wifi is disabled after hibernate - but just needs "Enable Wireless" from Network Manager right-click menu.
I never use standby anyway so can't comment on that.

0 problems with bluetooth, wifi and sound.
Except for the typical hibernate/standby problems all the hardware worked out of the box on my machine.

---

### Post by astrobob.tk on 2011-04-10
> **Sophont said:**
> My specs are in the signature.

I had to stay at Lucid because testing 10.10 with live cd didn't boot.

Otherwise hardly had any problems.

My wifi works with kernel driver:
Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh]

I kept windows on a reduced partition for games - looking forward to delete that when the open AMD drivers 3D acceleration for 4670 has matured. The proprietary driver mostly works - but not really good enough for games and no better than the free driver for 2D.
On my prior Inspiron 9400 with NVidia card games (EVE Online, DDO, Left 4 Dead) worked fine via wine for years (with prioprietary nvidia drivers).

Similar problems with hibernation. It kinda works but is glacially slow so I never bother and shutdown instead. Wifi is disabled after hibernate - but just needs "Enable Wireless" from Network Manager right-click menu.
I never use standby anyway so can't comment on that.

0 problems with bluetooth, wifi and sound.
Except for the typical hibernate/standby problems all the hardware worked out of the box on my machine.

Great :D

I recently found out the problem with the hibernation; It would be nice if you could confirm it:

after recovered from Hibernation or standby, use a terminal to run "top" & check whether "snort" is listed in the list of processes; it should be the one taking up all the cpu; it will not appear in the System Monitor.
If it does appear in top, try to "kill" the process & let me know if the cpu is back down to normal !!!

cheers

---

### Post by astrobob.tk on 2012-02-08
> **Sophont said:**
> My specs are in the signature.

I had to stay at Lucid because testing 10.10 with live cd didn't boot.

Otherwise hardly had any problems.

My wifi works with kernel driver:
Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh]

I kept windows on a reduced partition for games - looking forward to delete that when the open AMD drivers 3D acceleration for 4670 has matured. The proprietary driver mostly works - but not really good enough for games and no better than the free driver for 2D.
On my prior Inspiron 9400 with NVidia card games (EVE Online, DDO, Left 4 Dead) worked fine via wine for years (with prioprietary nvidia drivers).

Similar problems with hibernation. It kinda works but is glacially slow so I never bother and shutdown instead. Wifi is disabled after hibernate - but just needs "Enable Wireless" from Network Manager right-click menu.
I never use standby anyway so can't comment on that.

0 problems with bluetooth, wifi and sound.
Except for the typical hibernate/standby problems all the hardware worked out of the box on my machine.

Speaking of this, how's the "64-bit" Ubuntu on it? Am thinking of moving to 64 after testing it, but would like your say about it.

---

