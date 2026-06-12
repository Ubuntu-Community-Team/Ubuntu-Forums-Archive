---
title: "how to change the resolution in icewm?"
date: 2005-02-18
forum: Desktop Environments
---

### Post by hkl8324 on 2005-02-18
i have an old machine (P!!! 450Mhz) i find it too slow to run gnome, so i apt-got(?) icewm.

but heres the problem, icewm takes the highest resolution my vid card support, and that is 1680x1050(corrected), that the font is about 1.5mm tall. So is it not good to read.

how can i change the resolution to 1024x768?

plus, can i also change to GDM resolution to 1024x768?

thanks

---

### Post by Wim Sturkenboom on 2005-02-18
My feeling is that the resolution at that stage (when GDM starts) is based on the HorizSync and VertRefresh in */etc/X11/XF86Config-4*. If you change the highvalue of HorizSync, it will probably use lower resolution, but you will never be able to use a higher one.

Further, */etc/X11/XF86Config-4* contains some lines like
*modes "1600x1200" "1024x768"*
The sequence determines which one is used first and that way determines what IceWM will use be default.

---

### Post by rkn on 2005-02-18
You can edit your /etc/X11/XF86Config-4 file and find the "Screen" section and several "Display" subsections:

Remove the "1680x1200" from the Modes lines:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Selected Driver"
	Monitor		"ViewSonic PS775-2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		[COLOR=Blue]Modes	"1152x864" "1024x768" "800x600[/COLOR]"  
	EndSubSection
```

Bob

---

### Post by az on 2005-02-18
It is better to run
sudo dpkg-reconfigure xserver-xfree86
since the changes you make will then be kept when you update or upgrade your system.

---

### Post by rkn on 2005-02-18
[QUOTE=azz]It is better to run
sudo dpkg-reconfigure xserver-xfree86
since the changes you make will then be kept when you update or upgrade your system.[/QUOTE]

This is curious.  Are you saying that If I modify my XF86Config-4 file that the changes I make to that file won't be saved if I up grade?  It has alway been saved before (with Debian).

That means that If I want to make a few simple configuration changes then  I should go through the xserver reconfiguration.  This involves going through the exercize of re-doing stuff like setting up my mouse, monitor and graphics card when all I want to do is change my display settings!!

Bob

---

