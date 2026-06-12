---
title: "Low resolution"
date: 2005-09-22
forum: Desktop Environments
---

### Post by TomBentley on 2005-09-22
I installed Hoary last night and I'm having problems using any resolution other than 600x400. I'd like to be using 1280x1024.

I'm using the graphics card (82854G) built into my intel D865GLC mainboard.

I've got a Samsung 193T 19" LCD monitor.

Having googled around a bit, I see people have had resolution problems with both this monitor and graphics card.

I've tried reconfiguring xorg using [HTML]<code>dpkg-reconfigure xserver-xorg</code>[/HTML], and I've also tried hacking xorg.conf by hand, but with no joy. My current xorg.conf is attached.

Any ideas?

---

### Post by Xian on 2005-09-22
In your xorg.conf this is your problem:

```
Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection
```

You need the HorizSync and VertRefresh rates.
They are provided by your monitor manufacturer.

This is how it should look (just an example):

```
Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
        HorizSync       30-70
        VertRefresh     50-140
EndSection
```

---

### Post by TomBentley on 2005-09-22
> You need the HorizSync and VertRefresh rates.
They are provided by your monitor manufacturer.

I just tried that (using the values for my monitor, 30-81 and 56-75), and I get 'video mode not supported' floating around the screen, and no gnome login. 

Then, as an experiment, I tried it at 1024x768, and that seems to work OK.

Looks like the monitor doesn't like something (at 1280x1024), but since I got those values from the monitor docs, I'm not sure what the problem is.

---

### Post by heimo on 2005-09-22
Check these:
[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)
[http://ubuntuforums.org/showthread.php?t=24923](http://ubuntuforums.org/showthread.php?t=24923)

You could also try Breezy Live CD and if it works flawlessly, consider upgrading early. (it's still in development, but works already quite nicely)

---

### Post by dbott67 on 2005-09-22
[QUOTE=heimo]Check these:
[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)
[http://ubuntuforums.org/showthread.php?t=24923](http://ubuntuforums.org/showthread.php?t=24923)

You could also try Breezy Live CD and if it works flawlessly, consider upgrading early. (it's still in development, but works already quite nicely)[/QUOTE]

This is one of the tricks I use.  If the Live CD (Breezy, Hoary, Knoppix... pick your fave) works and allows you to change the refresh rate/resolution to your desired settings then copy it to floppy/USB drive/e-mail/print the xorg.conf file and copy it to your installed distro.

-Dave

---

### Post by dbott67 on 2005-09-22
[QUOTE=dbott67]This is one of the tricks I use.  If the Live CD (Breezy, Hoary, Knoppix... pick your fave) works and allows you to change the refresh rate/resolution to your desired settings then copy it to floppy/USB drive/e-mail/print the xorg.conf file and copy it to your installed distro.

-Dave[/QUOTE]

On my Toshiba Laptop, I had to add the following lines (in bold) to my xorg.conf file.  Keep in mind that your settings will be different:

After fresh installation of Ubuntu 5.04, video resolution was only 640x480 with 1" black band along right side and 1/4" along bottom. Issue appears to be related to hsync & vsync, as well as Modeline settings. Secondary issue with performance may be related to default colour depth of 24 (changing colour depth to 16 increases performance noticably).

1. Edit /etc/X11/xorg.conf

Added/changed the following lines in "Monitor" Section:

Section "Monitor"
Identifier "Generic Monitor"
[I][B]HorizSync 30-64
VertRefresh 50-100[/B][/I]
Option "DPMS"
[I][B]Modeline "640x480" 25.175 640 664 760 800 480 491 493 525 #60Hz
Modeline "800x600" 40 800 848 968 1056 600 601 605 628 +hsync +vsync
Modeline "1024x768" 65 1024 1032 1176 1344 768 771 777 806 -hsync -vsync[/B][/I]
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NeoMagic Corporation NM2200 [MagicGraph 256AV]"
Monitor "Generic Monitor"
***DefaultDepth 16***

2. Save file and restart

I'm no expert by any stretch of the imagination, but it may help to give you a few other areas to look at.

---

### Post by TomBentley on 2005-09-22
[QUOTE=dbott67]This is one of the tricks I use.  If the Live CD (Breezy, Hoary, Knoppix... pick your fave) works and allows you to change the refresh rate/resolution to your desired settings then copy it to floppy/USB drive/e-mail/print the xorg.conf file and copy it to your installed distro.[/QUOTE]

 I tired the Breezy live CD preview, and 1280x1024 worked out of the box  :smile: , but using the xorg.conf from that with Hoary didn't work.  :neutral:

I guess can manage with 1024x768 for now, and wait till Breezy-proper comes out.

Thanks all!

Tom

---

