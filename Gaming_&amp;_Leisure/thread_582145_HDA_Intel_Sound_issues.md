---
title: "HDA Intel Sound issues"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by pyrokenx on 2007-10-19
Hi all, I have been experiencing this problem ever since edgy on my thinkpad T60, I always hoped it would be an issue that would go away sooner or later in some new version of something I updated, or in a new version of ubuntu, but it doesnt.

I havent used any other distributions to see if this is an ubuntu problem or just a linux problem all-around.

My sound is jittery and crackles when playing games, when playing music or movies or youtube everything works perfectly, even when there are multiple sounds going, but whenever I run a game it all of the sudden goes very jagged

warsow and many other games are nightmares and warsow actually crashes when I have sound enabled.  I have looked and looked for advice on how to fix this including installing the latest alsa from source and editing the options etc etc, I checked that the modem was enabled, I cant disable the sound, I even tried with the modem disabled.

Any help would be appreciated :)

EDIT: one last thing, not all games do it.

My info:

IBM (Lenovo) Thinkpad T60 14"
Intel GMA 945 video
Ubuntu 7.10 (Gutsy) x86_64 (note that problem occurs in 32-bit as well)


MY LSPCI:
```
jeffj@jeff-thinkpad:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
jeffj@jeff-thinkpad:~$ 
```

Thanks in advance everyone.

EDIT: one last thing, not all games do it

---

### Post by pyrokenx on 2007-10-21
*bump*

Anyone? :-/

---

### Post by suupaabaka on 2007-10-22
I have the same problem... and it's weird how movies/music isn't affected in any way.

---

### Post by pyrokenx on 2007-10-23
*bump again*

I wont bump this again guys, I just seem pretty lost by this problem and cant understand why its even happening, anyone?

Anyone else experiencing the same issues who has resolved them?

I am not sure if it was submitted as a bug, I've seen similar bugs in launchpad that were associated with hda intel sound, but none of the fixes anyone has come up with has helped my situation thus far..

---

### Post by DDuong on 2007-10-24
Are you using Wine to play these games?

If so, I recommended changing the following options in the Audio tab in the winecfg:

> 
Hardware Acceleration
Default Sample Rate
Default bits per Sample


Changing them around would help a bit

---

### Post by pyrokenx on 2007-10-24
***PARTIALLY SOLVED***

 
Not using wine, they are linux games.

I think the issue only happens when using OSS sound.


Anywho, I have solved the issue myself by building and installing a new alsa from source.  There are some quirks still here and there but my sound bugs in warsow have dissapeared, and alien arena doesnt sound bad if you use 'maximum compatibility' mode.

Using module assistant was the method I chose.

```

sudo aptitude install module-assistant build-essential
cd /usr/src
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa
sudo shutdown -r now

```

loosely following this wiki article:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

suupaabaka, please confirm for me this works :)

---

### Post by suupaabaka on 2007-10-25
Hmmmm... it didn't do anything for me. Maybe I did something wrong. I'll give it another shot in the morning.

---

