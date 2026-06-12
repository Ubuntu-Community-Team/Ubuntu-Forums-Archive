---
title: "Screen rotation breaks desktop (Xserver)"
date: 2009-02-24
forum: Desktop Environments
---

### Post by antoinedl on 2009-02-24
Hi everyone,

I'll just go ahead and explain what I did and how everything is right now, because it seems pretty complicated to me.

After installer the fglrx driver (on a Ati X2300, HP Compaq 6910p laptop), I decided to try the features (compiz, available resolutions), and because I know a little bit how the xorg.conf file works (and because of the fact that I know that in Intrepid, xorg.conf is almost empty)...

So this is it, I tried the screen rotation in the Screen Resolution Manager (System--Preference-- Window/Screen Resolution manager ), I'm sorry, I cannot look, you'll understand why in a few seconds.

The screen became dark, and then I re-opened (rotated 90 degrees clockwise, the way I asked), but there was a big black stripe on the left side of my screen.  I would have liked to fix this by using the same menu that brought me there, but everything on my desktop had disappeared : the 2 menu bars, my hard drives icons, and I couldn't even access the terminal with my shortcut keys !

I told to myself that I could just restart the Xserver (ctrl-alt-backspace), but when everything reloaded, it was just the same.  I tried the terminal (ctrl-alt-F2 (3-4-5-6)) but I need a GUI to open the menu and reset the rotation !

I also tried "xfix" in the recuperation tool (with GRUB), but it didn't work.  I finally tried "sudo aticonfig --initial -f" after having deleter xorg.conf (because it that command makes a brand new, shiny xorg.conf file), but this didn't work either...


If someone know how I could fix this, please !

Thanks a lot !

---

### Post by notoriousdbp on 2009-03-24
Same here on 9.04 alpha again with fglrx drivers installed (writing this in 8.10 by the way)

---

### Post by bigbencg on 2009-03-25
I have been dealing with several display issues lately, and I may be able to help.  I had a problem with a monitor connected to a KVM, where the display would be "shifted" to the right leaving a 1 inch black strip on the screen.  To get the screen back to a format you can work with you can use the command xrandr.  Right click on your desktop and select "Run Command".  In the resulting window type terminal, an icon for terminal may appear, and press enter.  This will open a terminal on the desktop that you can hopefully see or at least move if needed.  

In the terminal type
```
xrandr -q
```

The resulting information is a list of supported display modes and the name of the output adapter.  The output may have been listed in xorg.conf as LVDM or LDVM or something to that affect.  Other names may include default, DVI1, VGA, HDMI......and so on, but it will be the first thing in the second line.  In my example my output is called "default" even though it is an HDMI port.

```
bigben@8151-KUBU:~$ xrandr -q
Screen 0: minimum 800 x 600, current 1920 x 1200, maximum 1920 x 1200
default connected 1920x1200+0+0 0mm x 0mm
   1920x1200      50.0*    51.0
   1600x1200      52.0
   960x600        53.0
   800x600        54.0

```

Whatever the name of the output you will need to use it in the following command, substituting default for your outputs name.

```
xrandr --output default --rotate normal
```

That should re-orientate your display.  Your problem was caused by an incorrect Vsync or Hsync setting, try adding those specs to xorg.conf under the "Monitor" section.  In the example below are the specs for the monitor I was having trouble with.

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30-83
	VertRefresh	55-75
EndSection

```

You can either restart X or just restart the computer so those take affect and try rotating your screen again.  This time use the terminal and xrandr command, that will allow you to make changes on the fly and change back if needed.  Use the command above but use right or left in place of normal.  Right = CW and Left = CCW, Invert = Upside Down, Normal = 0 degrees.  If you rotate and the display is still shifted off screen, you can try setting different refresh rates using xrandr

Query xrandr for current mode and rate
```
xrandr -q
```
a * will be next to the current mode and rate listed.  Then try
```
xrandr --output default --rate xx
```
substituting xx with another rate your monitor can support.  If you are currenty at 75 Hz, try 74 or 70 or 60 or 85, your display should have a range of rates it can handle.  Once you find a rate that gives you a good display you can generate a modeline using gtf

```
gtf 1024 768 60
```
gtf width height rate, below is an example output.

```
bigben@8151-KUBU:~$ gtf 1920 1200 50
gtf 1920 1200 50

  # 1920x1200 @ 50.00 Hz (GTF) hsync: 61.75 kHz; pclk: 158.08 MHz
  Modeline "1920x1200_50.00"  158.08  1920 2032 2240 2560  1200 1201 1204 1235  -HSync +Vsync

```

Copy those two lines into xorg.conf into the Monitor section.  That should list that display mode in whatever graphical screen utility you use.

If you want to set that as the default mode you can specify that under the "Screen" section in xorg.conf

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	[B]SubSection "Display"
		Depth	24
		Modes	"1920x1200_50.00"
	EndSubSection[/B]
EndSection
```

I specified a color depth in the example, it may not be necessary to do so, but the modes line is, use the name created by gtf.

---

### Post by bigbencg on 2009-03-25
One more thing about xrandr, it is a per session utility, meaning any changes you make in xrandr will only stay in effect until X is restarted.  If you set a mode and loose video, restarting X or the computer will null the xrandr command.

---

### Post by andrew frank on 2011-01-05
i have a similar problem (black band at the bootom after rotation - the display seems to be shifted up and extends beyond the top).
experimenting with the rates did not do anything for me (but i am on 10.10).

any other suggestions what could be the problem? it seems that the origin for the up/down display coordinates is set wrong.

andrew

---

