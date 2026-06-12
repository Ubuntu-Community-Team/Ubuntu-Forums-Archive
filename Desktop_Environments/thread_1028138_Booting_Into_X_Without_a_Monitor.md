---
title: "Booting Into X Without a Monitor"
date: 2009-01-02
forum: Desktop Environments
---

### Post by mojorising on 2009-01-02
Hi! I'm trying to boot Ubuntu with XFCE (actually Mythbuntu) into X Window without a monitor. 

The system needs to boot into X because, eventually, I will hook a projector to this machine and occasionally watch movies on it. So I can't disable GDM or only run an X server that other systems connect to. 

I've Googled around and checked these forums quite a bit and haven't found anything that works for me just yet. This post at [http://ubuntuforums.org/showthread.php?t=51587&page=2](http://ubuntuforums.org/showthread.php?t=51587&page=2) had several suggestions/ work-arounds but none of them worked for me and they aren't what I would call a very "clean" solution. 

Upon checking my xorg.conf file (contents of which printed below my message, sans the file's comments), I see it looks a good bit different than those I have seen in the past as it is relatively sparse. My feeling is that this is because many things that used to be set by the conf file in previous versions are now automatically detected at X startup. I am wondering if there are proven settings I can lock in on my xorg.conf file that will enable me to consistently fire up XFCE like I'm trying to. 

Does anyone out there have any ideas on how I can accomplish my goal? Thanks for any help in advance and happy new year.  :)


Mike


My xorg.conf file (comments removed):
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```


P.S. My video setup includes an Intel 945 video adapter and a Samsung SyncMaster monitor (which may occasionally be connected until I get the projector).

---

### Post by mojorising on 2009-01-11
ping. 

Anyone out there have any useful input on this one? I (and no doubt at least a few others) would greatly appreciate it.


Mike

---

### Post by AboveTheLogic on 2009-06-20
I'm wondering what it is you are trying to accomplish.

I run mythbuntu myself and left the default GDM (xfce) session handling on the physical screen alone. When I need to access it remotely, I use FreeNX to log into a KDE session.

This allows me to access the machine remotely and do whatever I want to do in the background, while the console session for the TV is left untouched.... actually my wife can be watching TV or a movie while I'm messing around with KDE in the background...

---

