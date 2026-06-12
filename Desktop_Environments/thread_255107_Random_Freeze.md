---
title: "Random Freeze"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Hatty on 2006-09-10
Every once in a while, about every two days, Ubuntu freezes. I can move the mouse but nothing responds to clicking. XMMS will stop playing, but randomly (every few minutes) it'll play a second or two.

This last time I left System Monitor open to see if anything was eating up CPU power or RAM. Nothing was.

All I keep running is XMMS and aMSN, maybe firefox or gnome-terminal (most likely running irssi).

I really love this distro and if someone would help me debug this problem, I'll never leave.

Heres the info from lspci:
```
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
```

-Hatty

---

### Post by vbgunz on 2006-09-11
I am not sure if this applies or if this is exactly what fixed my problem *but* I did have a problem similar to yours and it was sickening. What I believed fixed it was to go into System > Administration > Networking and disabling + deactivating all connections *but* the one I actually needed...

Not sure if this is the issue or if it was pure coincidence *but* I guess it won't hurt to try. Good luck!

---

### Post by Hatty on 2006-09-11
vbgunz: The only connection I have enabled is my eth0.

-Hatty

---

### Post by vbgunz on 2006-09-11
I had your same exact experience and I actually began to hate Ubuntu for it. I asked all over about it on IRC and was told it could be a failing graphics card *but* this was far from the truth in my case (*but* may be in your case). I was also told to run memcheck on the grub boot screen cause one of my memory sticks could have been failing and I did for about 36 hours *but* I still saw no error (*but* may be in your case). Also, my freeze ups took place on Dapper Flight. Could Dapper either be outdated OR are you using Edgy?

Freezups suck and I hope you solve it cause I'll admit nothing can be worse :( At worse, I just bumped up post :)

---

### Post by Hatty on 2006-09-11
> **vbgunz said:**
> Could Dapper either be outdated OR are you using Edgy?
I installed with the Dapper CD I ordered from ShipIt (6.06 LTS).


> **vbgunz said:**
> I was also told to run memcheck on the grub boot screen cause one of my memory sticks could have been failing and I did for about 36 hours *but* I still saw no error (*but* may be in your case).
I'll run memcheck next time I boot up and post the results.

-Hatty

---

### Post by Hatty on 2006-09-14
Memtest86+ Results
```
WallTime:   65:29:03
Cached:     766M
RsvdMem:    1752k
Memcap:     e820-Std
Cache:      On
ECC:        Off
Test:       Std
Pass:       127
Errors:     0
ECC Errors: (Blank)
```

---

### Post by vbgunz on 2006-09-14
Now, hopefully someone can come along and offer some advice :) *bump*

---

### Post by Hatty on 2006-09-26
*bump*
I'd really like some help here...

Also, I switched to Rythymbox and it will just keep on playing, not freezing whilst everything else won't respond. The freezes seem to be happening more often, aswell.

-Hatty

---

### Post by vbgunz on 2006-09-27
Do you notice the freeze takes place right after launching a certain app? e.g., Since Rhythmbox keeps playing, can you still move the mouse cursor? If so, although you can move the mouse, you cannot select anything or switch desktops? If this is the case, switch to the console and kill the offending application. This happens to me sometimes with vlc (switching skins) and Gxine... Although it rarely happens, if I log into the console and kill the app and switch back, the freeze is gone. Could this be the case? It doesn't just need to happen with launching apps. It could be something an app does. I noticed this. If you can pinpoint the app, kill it and try filing a bug report. Also, since you might do a hard reboot, try killing some apps in the console while switching back and forth to see maybe you unfroze it? Just some suggestions. My 2 cents :)

---

### Post by Hatty on 2006-11-06
I just updated to Ubuntu Edgy and had hoped the problem would go away with the 2.6.17 kernel.

It didn't

It still does the same thing.

For the record I switched from Rythymbox to Amarok (v 1.4).

This time when the freeze happened, I had Amarok, GTK-Gnutella, Firefox(2.0),  and a gnome-terminal (2 tabs, one running irssi, one running vim (I think)).

Any help would be appreciated.

-Hatty

---

### Post by sigge on 2006-11-07
I have this same problem ever since switching to edgy... :( ](*,) 

What I would do, if I had a second computer on the network, is install and configure ssh on both pc's before the crash. Then upon freeze-up, I would use the other machine to try to log in through ssh.

If it works to log in, and one can run ls, cd and whatever remotely, then the problem is likely to lie within X, or more specifically, your videocard/driver.

The problem is, I have no second computer on this network... :-k 

Personally I'm running a Geforce 4 440 MX, wich is on the shy side of old, I know... :D  I'm also running Automatix nvidia drivers.

UPDATE!

I changed from nvidia to nv driver after posting this, 13 hours ago. Haven't had a freeze since. :)

---

