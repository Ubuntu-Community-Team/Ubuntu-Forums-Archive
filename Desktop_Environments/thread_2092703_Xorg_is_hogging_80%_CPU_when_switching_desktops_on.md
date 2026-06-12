---
title: "Xorg is hogging 80% CPU when switching desktops on Unity"
date: 2012-12-08
forum: Desktop Environments
---

### Post by LillyDragon on 2012-12-08
This is the only thing keeping me from using Unity more often than XFCE. I shouldn't have to hear my poor fan whine like crazy during normal desktop usage and drowning out my music. Considering how I organize program usage across multiple virtual desktops, (For instance, I keep Firefox or Chrome in the "Internet Space", Audacity for music in the "Music Space", GIMP or some other program in the "Workspace", etc.) I'm switching desktops constantly; that's how I use Linux, or else it's complete chaos with scattered windows everywhere, like on Windows without Dexpot, blegh.

tl;dr, long story short, Xorg's CPU usages spikes like crazy when switching desktops, and it doesn't stop after a few seconds either. I can understand that usage is going to spike, but it doesn't slow down until whole minutes *after* the fact! Is there anything I can disable that can ease it up? The only work around I can find needs a Xorg.conf, which Ubuntu doesn't seem to use anymore, what the tarnation?! D:

---

### Post by LillyDragon on 2012-12-10
[IMG]http://i1058.photobucket.com/albums/t410/johnluke728/snoopy_bump.jpg[/IMG]

Obligatory topic bump. =P I really can't figure this one out from searching on Google, so if anyone else has come across the issue and discovered a workaround, I would greatly appreciate it. XD

---

### Post by zombifier25 on 2012-12-11
It would be helpful if you post your system specs.

---

### Post by robert shearer on 2012-12-11
> The only work around I can find needs a Xorg.conf, which Ubuntu doesn't seem to use anymore

xorg options....
[http://www.ubuntututorials.com/location-xorg-conf-ubuntu/](http://www.ubuntututorials.com/location-xorg-conf-ubuntu/)

---

### Post by LillyDragon on 2012-12-11
Holy cow, how did I miss that page while Googling this. o__o Doesn't matter now, so thanks for linking me to it. ^^ I can't seem to find a xorg.conf.d in my /usr/lib/X11/ directory, so I'll try generating a Xorg configuration script myself with the provided command after lunch. It kinda sucks how everything isn't where it used to be a few years back!

> **zombifier25 said:**
> It would be helpful if you post your system specs.

Oh yeah, I hadn't thought about that. ^^' I'll dump relevent specs for my HP Laptop in code tags below. I'm also running Ubuntu through WUBI since I don't want to mess with the factory-default recovery partitions. (I'm peeved to no end that a Windows 7 disc wasn't included with my license key, otherwise I would be running both Windows and Ubuntu natively.)

```

Ubuntu 12.04 LTS - Kernal 3.2.0-34-generic

CPU       : Celeron(R) Dual-Core CPU       T3500  @ 2.10GHz
Memory    : 2941 MiB
Graphics  : Intel Corporation Mobile 4 Series Integrated Graphics Chipset (1GB of Video Memory)
Hard Disk : ATA Hitachi HTS54323

```

---

### Post by LillyDragon on 2012-12-14
Finally built up the nerve to try it, and nothing. ;___; The terminal spews out an error and doesn't create a Xorg.conf at all, ugh. So much for an easy fix! The only files that relate to Xorg.conf.d are input scripts in that folder, which has nothing to do with video output.

I also heard there's an option to disable Antistrorphic filtering, which might knock a dent in the CPU usage, but the video settings for that in Unity are proving difficult to find.

---

### Post by LillyDragon on 2013-08-02
Bumping the thread to say that I realized it wasn't Xorg's fault. Here's the way I have my desktop arranged : I had deviantART open in a Firefox window on Desktop 3, Skype on Desktop 4, GIMP on 1, and music apps on Desktop 2; I like keeping things organized.

While none of that affecting performance overall, deviantART was causing Firefox to use 10-14% of my CPU constantly, so it gave me the impression that my fan was going insane because of Xorg's occasional, but understandable CPU spikes of 80%, when really, that was never the case. So now I leave Firefox idle on a New Tab, so none of the websites I leave open hogs CPU while working on art, or playing games. The fan cools back down much more quickly this way, so I can use Unity or Xfce4 whenever I want without issue. It's solved now!

---

### Post by RadicaX on 2013-08-02
That was an interesting read. Sorry that happen to you in the first place. I can understand not wanting to delete your windows OS if you had no install CD. Sadly that is what my computer was like. My windows OS finally up and died though and have been using Xubuntu since. (Family loved Windows, just had to have Itunes. But now they for the most part prefer Xubuntu.) No more constant blue screens of death on this setup wahahahaha.  Some of the websites you can go to really make web browsers work hard. Facebook is like that too.

---

### Post by LillyDragon on 2013-08-03
Yeah, Facebook lags like crazy on me too. I'd say it's harder on the CPU than deviantART sometimes; even Tumblr and most web forums use as much CPU as dA. I needed AdBlock to cut back on some lag too, since a lot of ads make the entire page mostly unviewable from constant hiccups. After all that, I can only trust GameFAQs and Wikipedia not to do anything while idling.

Ouch, I know that feeling, it sucks not having the Windows CD. My cousin can relate too, I had to install Ubuntu with Xfce4 on his laptop after Windows stopped booting on him. (I think it's a registry problem.) He still hasn't gotten around to fix it with the dual-boot arrangement, since Ubuntu covers most of his needs.

---

### Post by RadicaX on 2013-08-03
Indeed. quite a few sites can do that. Mostly notice it on ones with sorta "live" format if you will. Where they are changing and doing things even when you are not doing nothing on so and so part oft he page. No script can help a lot too. (since it blocks everything till you allow.)

Basically how most feel once they do a Linux Distro, it covers most if not all their needs. Sometimes a program needs to die out before people will dare try anything else. (And at least your cousin can get any important files off the Windows os with Ubuntu.)

---

