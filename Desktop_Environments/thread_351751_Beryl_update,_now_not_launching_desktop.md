---
title: "Beryl update, now not launching desktop"
date: 2007-02-02
forum: Desktop Environments
---

### Post by fracktor on 2007-02-02
After installing the beryl updates yesterday, it no longer loads beryl, it just flashes for a second like its trying to load, and then just defaults back to metacity. I am running Ubuntu Edgy. I tried messing around with the gdm.conf  and also tried redoing the desktop file, 
sudo mkdir -p /etc/X11/sessions
sudo gedit /etc/X11/sessions/xgl.desktop
Now I cant get back into my desktop, none of the sessions work except for failsafe terminal.
Gnome doesnt work, default doesnt work, XGL doesnt work, failsafe gnome doesnt work. They all start to login, then just hangs at a blank screen. No errors or anything. I can only get into a terminal, but from the terminal I dont know what to do to ix this problem. Is there a way to reinstall gnome or XGL? Any ideas would be greatly appreciated. I am still new to linux so please bare with me.

---

### Post by Ramunas on 2007-02-02
Same problem here, I'll wait for an update. Lets hope this gets fixed soon.

---

### Post by waldorf on 2007-02-02
ditto except I updated about an hour ago

---

### Post by Ryba on 2007-02-02
I'm not sure about the XGL server but if you using the latest beryl with AIGLX (the one built into the xorg one that XGL runs on top of) then it works great. You cannot tell any difference at all between just xorg + beryl and the Xorg + Xgl + beryl

The Xgl to me seems like a totally useless layer that has some memory leaks as well.

Why don't you try removing all the Xgl stuff and just use normal Xorg + Beryl

1) comment out all that Xgl stuff from /etc/gdm/gdm-custom.conf
2) in the xorg.confg in the "ServerLayout" section enable the AIGLX option as such

```
Section "ServerLayout"
        Identifier      "AIGLX Layout"
        Screen          "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "AIGLX" "true"
EndSection
```3) Make sure composite is enabled as such

```
Section "Extensions"
        Option      "Composite" "Enable"
EndSection
```4) An optional but very nice performance enhancement is in the Device section enable the offscreen pixmaps (no clue what this does though but stuff goes faster) as such

```
Section "Device"
        Option          "XAANoOffscreenPixmaps" "true"
EndSection

```
Restart the xserver (sudo /etc/init.d/gdm restart) and you should be good to go.


If you used a script to only trigger "beryl-manager" whenever the Xgl was detected as the server then you can just run "beryl-manager" by hand and *then* everything will be just as before.

Otherwise your beryl-manager is probably already to go on startup and you will have everything working like you used to.

---

### Post by danhm on 2007-02-02
I had the same problem. I downgraded to the last version (0.1.99.2) by:

```

sudo apt-get remove 'beryl*'
sudo apt-get install beryl=0.1.99.2~0beryl1 beryl-core=0.1.99.2~0beryl1 beryl-manager=0.1.99.2~0beryl1 beryl-plugins=0.1.99.2~0beryl1 beryl-plugins-data=0.1.99.2~0beryl1 beryl-settings=0.1.99.2~0beryl1 beryl-settings-bindings=0.1.99.2~0beryl1 emerald=0.1.99.2~0beryl1 libberyldecoration0=0.1.99.2~0beryl1 libberylsettings0=0.1.99.2~0beryl1 libemeraldengine0=0.1.99.2~0beryl1 emerald-themes=0.1.99.2~0beryl1 -V

```

Should work fine if you don't mind the downgrade.

---

### Post by fracktor on 2007-02-02
Thanks for all the info, I am at work now, so I will try those solutions as soon as I get home (can't wait). I will post later to let you know my solution....

---

### Post by frodeeike on 2007-02-02
thank you!

works like a charm.

---

### Post by waldorf on 2007-02-02
A complete removal and then re-install seemed to solve the problem for me.

---

### Post by fracktor on 2007-02-02
I removed beryl and that didn't work.
Now when I start ubuntu, I get a black screen with a login that looks like a dos prompt. I can login but their is no gui what so ever. I there a way to reinstall the gui for the desktop login?

---

### Post by fracktor on 2007-02-02
I think it may have to do with gdm or gnome, I am not sure though. Is their a way to reinstall it?

---

### Post by fracktor on 2007-02-02
I found this post
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

Which relates to my problem, I am going to give that a try now. If anyone else has any ideas, please let me know, it would be greatly appreciated...

---

### Post by fracktor on 2007-02-02
I am still getting no gui at login.
I tried running
sudo dpkg-reconfigure xserver-xorg
and then ran
sudo /etc/init.d/gdm start
nothing happens, no errors.
I am kind of at a lost as to what to do now. Any help is much appreciated....

---

### Post by CroEragon on 2007-02-02
Same here. But guys i wouldn't bother to try repair it. This is second time update  screwed my beryl, and im not surprised, it is beta ( but even so its beta somebody should test updates before offering it to update). Know solution is to downgrade, but anything can go wrong, so just wait another update that fix it and thats it. You can live without beryl 2 days

---

### Post by fracktor on 2007-02-02
I can live without beryl, yes, but I would like to have my desktop back still...

---

### Post by gibbylinks on 2007-02-03
Same problem here, I've just changed my xorg.conf back to nv,  and will live with metacity until a fix comes out.

There's also a couple of posts about this on the beryl forum ([http://forum.beryl-project.org/)]("http://forum.beryl-project.org/"). Most people seem to be rolling back to an earlier version.

:-({|=

---

### Post by shador on 2007-02-03
> **Ryba said:**
> I'm not sure about the XGL server but if you using the latest beryl with AIGLX (the one built into the xorg one that XGL runs on top of) then it works great. You cannot tell any difference at all between just xorg + beryl and the Xorg + Xgl + beryl

The Xgl to me seems like a totally useless layer that has some memory leaks as well.

Why don't you try removing all the Xgl stuff and just use normal Xorg + Beryl



Your fix only works for Nvidia cards right? I thought ATI stuff didn't work with composition enabled.

---

### Post by naseem on 2007-02-03
I had similar problem and solved updating all beryl staff from trevino sources.list repos, might help you too ):P

---

### Post by bornakke on 2007-02-06
I have a similar problem, but i'm not sure its the same. 

Did the Beryl upgrad from 1.99.2 to 1.9999 the other day, which seems to have broken my XGL session. Running gnome without XGL shows no problems using glxinfo (or gears):

> display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI

[...]
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
[...]
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


However I get no Hardwear rendering when I log into my XGL session:
> 
name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
[...]
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
[...]
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


Also the following new errors are shown in the xorg.0.log :
> 
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32


I'm using ATI 9000 mobility, which shouldn't support Aiglx, which is why i'm thinking that the error might have something to do with the computer trying to use Aiglx. 

My Xorg.conf information is:
> 
[...]
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
[...]
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
[...]
Section "DRI"
	Mode	0666
EndSection


I'm still a newbee to Ubuntu but *Ryba* writes that you should comment out all Xgl stuf in gdm-custom.conf, but I have no information in that file at all &#8211; could that have something to do with the solution? :confused: 

I have tried downgrading, upgrading and removing Beryl, but it doesn't seem to have any effect what so ever on my problem!

Any help would be more than gladly appreciated!

---

### Post by padlefot on 2007-02-15
worked as a charm, all uptdates =)

---

