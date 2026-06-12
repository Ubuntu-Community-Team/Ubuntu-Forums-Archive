---
title: "system tray icons messed up"
date: 2008-08-04
forum: Desktop Environments
---

### Post by jasidog on 2008-08-04
Not quite sure how to explain this other than by posting an image so here goes.

The icons start off fine but as new icons show up and the old ones shift position this messed up look occurs. With sort of ghost images of several icons in the same position. Closing an application that has an icon in the sys tray restores a clean normal look. 

Other ways to solve it include messing about with the panel settings. 

However these are temporary fixes until any icons are moved about again buy something new showing up in the system tray.

Anyone else come across this? 

I've had the issue ever since I installed 8.04 when it came out never had this issue in previous versions of Ubuntu.

---

### Post by kidux on 2008-08-05
I was having a similar probelm with AWN until I realized I had 3 different instances of it running. That may be what's happening here. Check to see if there are more than 1 systray loaded.

---

### Post by jasidog on 2008-08-05
No it doesn't seem to be that Kidux. I can remove the "notifacation area" and then replace it with a new one and still end up with the same issue. 

Plus two don't show in quite the same space. The 2nd will always show no icons. 

Thanks for the suggestion though Kidux, it's appreciated. :)

---

### Post by sayakb on 2008-08-05
Try adjusting the panel width. Also, see if by changing the icon theme, it does not get messed up.

---

### Post by jasidog on 2008-08-05
Thanks for the suggestions LinuxIsInnovation. :)

I know already that width or visibility (It's usually hidden till mouse over for me.) doesn't effect the problem.

I'll try a different icon theme though. Still I'm not too hopeful it will work because most of the icons, maybe all aren't effected by changing icon theme.

I'll get back to you on that though.

My own guess is it may be something to do with the way things are drawn so I'm going to try without compositing stuff like that too and see what happens.

---

### Post by jasidog on 2008-08-05
Well it's not conclusive because I've not tested for long enough. But it seems like when compositing is turned off the problem goes away. 

Doesn't really give me a solution with compositing on but it's interesting.

---

### Post by sayakb on 2008-08-05
Which card do you have?
At a terminal, do:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jasidog on 2008-08-05
Hi again LinuxIsInnovation! :)

I have an Nvidia GeForce 7600 GS.

If I run the reconfig of the the display settings like you asked. All that happens is that compositing is turned off and my screen resolution is minuscule.

Of course that solves the issue as compositing is off. But it doesn't help when it's resetup. 

By the way the only differences in my old xorg.conf and a reconfigured one are - 

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection
```

Which is needed for the proprietary nvidia drivers for compiz.


And also - 

```
Section "Module"
	Load		"glx"
EndSection
```

Which is also needed for that I assume.


Thanks for trying to help me though. :)

---

