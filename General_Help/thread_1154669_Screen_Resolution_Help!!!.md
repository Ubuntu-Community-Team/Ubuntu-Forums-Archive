---
title: "Screen Resolution Help!!!"
date: 2009-05-10
forum: General Help
---

### Post by Jeyaganeshdj on 2009-05-10
Hi All,

I had upgraded from 8.10 to 9.04 today and when i upgraded there was an warning message saying FGLRX graphics driver will not be supported and i ignored and continued to upgrade. The problem now is i cannot find a driver and so cannot set my screen resolution... Kindly help me out... If i cannot find any driver is the only solution is to downgrade my Ubuntu version???

---

### Post by Legace on 2009-05-10
> **Jeyaganeshdj said:**
> Hi All,

I had upgraded from 8.10 to 9.04 today and when i upgraded there was an warning message saying FGLRX graphics driver will not be supported and i ignored and continued to upgrade. The problem now is i cannot find a driver and so cannot set my screen resolution... Kindly help me out... If i cannot find any driver is the only solution is to downgrade my Ubuntu version???

What's your graphics card? Enter the following into terminal and post output here.
```
lspci -nn | grep VGA
```

Post your contents of the x.org file.
To do so, open Terminal, enter the follow and copy paste the contents of the Text editor here..
```
sudo gedit /etc/X11/xorg.conf
```

And what resolution do you want?

---

### Post by Jeyaganeshdj on 2009-05-10
Hi,

Please find the output... 1024x768 is good for me...

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200] [1002:5a61]

xorg.conf

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"ati"
EndSection

---

### Post by Legace on 2009-05-10
Do the following:

```
sudo gedit /etc/X11/xorg.conf
```

Then copy paste the following into the xorg.conf.

```

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
	SubSection "Display"
	Modes      "1024x768"
	EndSubSection
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "ati"
EndSection 
```

Save and reboot your PC. Now you should be able to set the resolution you want.. :)

---

### Post by Jeyaganeshdj on 2009-05-10
Hi,

 I have configured as you told, but the resolution is set only in the login page where I provide my user name and password... when i login to ubuntu the resolution problem still persists... any other way exists?

---

### Post by MarkX on 2009-05-13
Same problem here, as usual with Ubuntu! This resolution nonsense happens to me all the time and is always a pain fix.


This time it's even more difficult because I'm using a small keyboard with spanish layout and can't even find the right keys to work in the terminal!  

About time somebody put a working resolution changer in the "systems" menu. I'm not interested in "cloud computing", I'd just like the resolution to be at least easily fixable when it's wrongly detected. ... Please.

I can't even select option because the bottoms of windows don't show at 640x480

---

