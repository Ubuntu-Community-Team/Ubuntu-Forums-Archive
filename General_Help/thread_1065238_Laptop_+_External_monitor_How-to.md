---
title: "Laptop + External monitor: How-to?"
date: 2009-02-09
forum: General Help
---

### Post by benoitcsirois on 2009-02-09
I have an Intel chipset video card that support video-out. I want to extend my desktop to the other monitor (as opposed to the default desktop-cloning behaviour), but it seems there are no simple ways to do so.

I use Xubuntu 8.10.

I tried using *[FONT="Courier New"]xrandr --output VGA --auto --left-of LVDS[/FONT]*
And I was getting "*[FONT="Courier New"]xrandr: screen cannot be larger than(...)[/FONT]*"

According to [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#xorg.conf](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#xorg.conf) , I have to edit my xorg.conf, but the content is actually almost empty.

Here is the current content of my xorg.conf (I tried *[FONT="Courier New"]sudo dpkg-reconfigure -phigh xserver-xorg[/FONT]* but it remains the same)

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Anyone has any idea? Does Intrepid Ibex handle Xorg's configuration file differently? Any GUI tool to help me do what I want to do?

---

### Post by nacho-wan on 2009-02-21
It seems so empty because in Intrepid X11 works with some sort of autoconfiguration. This means that the system requires a lot less information written on the xorg.conf file.

However to get both monitors working as an extended desktop, you still have to declare the "size" of a virtual monitor that can hold both screens.

In my case, I edited the screen section as follows:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
		Virtual	2720 1024
	EndSubSection
EndSection
```

Now, in my case at least, xrandr works most of the time, but when I send a command to close the second monitor input sometimes it crashes X throwing me to the user welcome screen. Does somebody has the same problem?

---

### Post by bukwirm on 2009-02-21
Some (maybe all?) Intel graphic accelerators have a maximum size for the virtual display. What model do you have? You can find out with *lshw -C display*.

---

### Post by nacho-wan on 2009-02-22
> **bukwirm said:**
> Some (maybe all?) Intel graphic accelerators have a maximum size for the virtual display. What model do you have? You can find out with *lshw -C display*.

```
 Mobile GM965/GL960 Integrated Graphics Controller
```

---

