---
title: "Graphics rendering in X slower than Windows?"
date: 2009-01-07
forum: Desktop Environments
---

### Post by c0rv1d on 2009-01-07
Hi All

I have been a Windows user for many years and recently made my final big move to Linux. I'm starting to get comfortable with it, but there is one thing thats been bothering me for quite a while now. I have now installed xubuntu / xfce to try and make my system as lightweight and responsive as possible...

I have my video drivers set up properly (restricted nVidia) etc, but I still feel that whenever moving large chunks of video data around on the desktop (for example when scrolling up/down in a terminal with long log outputs or browsing my thunderbird inbox), it is choppy or kinda lagging which isn't the case with Windows. This has been my experience with various linux distros / window managers.

Is this "normal" in Linux? Are you guys experiencing the same, or can it just be my driver config etc?

Derek

---

### Post by syms on 2009-01-07
> **c0rv1d said:**
> Hi All

I have been a Windows user for many years and recently made my final big move to Linux. I'm starting to get comfortable with it, but there is one thing thats been bothering me for quite a while now. I have now installed xubuntu / xfce to try and make my system as lightweight and responsive as possible...

I have my video drivers set up properly (restricted nVidia) etc, but I still feel that whenever moving large chunks of video data around on the desktop (for example when scrolling up/down in a terminal with long log outputs or browsing my thunderbird inbox), it is choppy or kinda lagging which isn't the case with Windows. This has been my experience with various linux distros / window managers.

Is this "normal" in Linux? Are you guys experiencing the same, or can it just be my driver config etc?

Derek
try to type in terminal:
```
sudo mousepad /etc/X11/xorg.conf
```
then find line "Device" and in "options" subline add this line:
```
Option 	     "AccelMethod" 		"EXA"
```
heres my example:
```
Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"radeon"
	Option 	     "AccelMethod" 		"EXA"
```

well yes, xubuntu is still slower than windows, if you want system which is as fast as windows xp (or even faster) then try arch linux with xfce, it will be really super duper fast

---

### Post by c0rv1d on 2009-01-07
Thanks syms

I have done this, but unfortunately no difference :-k

Here is a dump of my xorg.conf. Don't know if this might shed some light on the topic...

```


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
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option	"AccelMethod" 	"EXA"
EndSection

```

Cheers D

---

### Post by weblordpepe on 2009-01-07
Oddly enough - I have heard this complaint before from a few people & even experienced it myself.

I don't really know if theres a single cause of it, but it is definitely to do with configuration of the video driver. 

One thing of note is that compiz / composit window managers can help a big deal...and hurt a bit too. Its worth having a look into to see whats right for you.

Sorry I couldn't be too much help :) But hey...lets see someone try to rip out the display engine & tweak it in Windows :P

---

### Post by denham2010 on 2009-01-08
Hi, just a thought, I notice you are loading glx in your xorg. Anyone correct me if I am wrong, but I believe glx is notorious for causing graphics issues. There are alternatives, such as aiglx, which perform much better.

Cheers.

---

### Post by theApokalypsis on 2009-01-08
Nvidia's restricted glrx drivers with Compiz...

 (EDIT: oops, just noticed lol you had xfce, i was using Gnome/Compiz with my experience)


...have very shotty 2-d performance from my experience with Geforce 9600GT. I went nuts with heavy Javascript apps in Firefox. Using the OSS drivers had a better performance gain I suggest using them.

Switched to ATI, however still awaiting DRI2 for accelerated video playback the performance issues I had with Nvidia are resolved and worth it. Not to mention AMD is keeping their promise with the recent R600/700 docs release to OSS. :)

---

### Post by c0rv1d on 2009-01-08
> **denham2010 said:**
> Hi, just a thought, I notice you are loading glx in your xorg. Anyone correct me if I am wrong, but I believe glx is notorious for causing graphics issues. There are alternatives, such as aiglx, which perform much better.

Cheers.

Cool! Well, what would it take to try and load aiglx? Shouldn't I have the aiglx module somewhere on my system / compiled in my kernel before changing it to aiglx in my xorg.conf?

---

