---
title: "Screen Not Looking Too Great"
date: 2008-08-06
forum: Desktop Environments
---

### Post by SeanHagen on 2008-08-06
So I've been using Ubuntu Hardy Heron for a while, and I'm fairly pleased. After I finished installing though, I had to do some tweaking to get X.Org to display at my LCD's native resolution, 1440x900. The LCD is a 19" Acer AL1916W, max resolution is 1440x900. This worked fine for my desktop, everything worked. 

One thing I noticed though, was that the login screen didn't display properly, but that didn't bother me. The bottom of the screen was cutoff, but since I always logged out using the red power button in the Gnome desktop to power off my computer. After a while though, I grew tired of Gnome, and wanted to switch back to my favorite window manager, Fluxbox. I also got tired of the default GDM login screen, so I found a nice theme and installed it. Long story short, I no longer had the red X button, and the shutdown menu for GDM was out of my reach. So after hacking my X.Org config again, I got GDM to display properly ( I think there was a "Viewport" line that was screwing it up ).

But now, the fonts are nearly unreadable, in Gnome or Fluxbox.

I've been trying to figure this out for a few days now, but no luck. It seems like my fonts are being compressed or something when they're shown on screen. If I open an XTerm window, and move it slowly one pixel at a time left or right, different characters will become unreadable and then readable as a move the window. This is happening to all of my fonts, in all of my applications. I'd switch back to my old X.org config... but I overwrote my backup by accident ( stupid mistake, I know ).

Here's the Screen, Monitor, and Device sections from my X.Org config:
```

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Acer"
        ModelName    "AL1916W"
        Horizsync    30.0-82.0
        Vertrefresh  56.0-76.0
        DisplaySize 366 229
        Modeline "1440x900" 136.0 1440 1520 1672 1904 900 903 909 934 +hsync +vsync
        Gamma 1.0
EndSection

Section "Device"
        Identifier  "Card0"
        Driver      "fglrx"
        VendorName  "ATI Technologies Inc"
        BoardName   "Radeon X1200 Series"
        BusID       "PCI:1:5:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        Defaultdepth 24
        SubSection "Display"
                Depth     24
                Modes "1440x900"
        EndSubSection
EndSection

```

I don't know if it's the font settings in X.org, although adding the following lines to the X.Org config didn't help:

```

Section "Files"
        RgbPath      "/etc/X11/rgb"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```

I've also attached an image that I took with my digital camera. Screenshots looked fine when viewed from other computers, but hopefully the pictures will illustrate what I'm trying to say.

See how the lowercase 'm' is compressed? It looks like an n! Or at least it does, when viewing the screen from a comfortable distance. But I'd rather not have to lean in and squint while coding! :p The same thing happens to several other characters, like " ( which looks like ' on my screen ).
[IMG]http://seanhagen.ipower.com/font_distortion.jpeg[/IMG]

Look at the 'p' and the '$' character. In the first picture, you can barely tell that it's supposed to be a 'p'. Also, the as I move the aterm, the font looks fine ( kinda bold in the picture ) to barely legeble ( really thin in the picture ).
[IMG]http://seanhagen.ipower.com/aterm_moving.jpeg[/IMG]

I've tried changing the fonts that xterm and aterm are using with the -fn switch, but all the ones I've tried end up with l o t s  o f  s p a c e s  b e t w e e n  t h e  c h a r a c t e r s. :-?

If I need to turn on ClearType or any other sort of font-smoothing, just point me to a good tutorial, and I should be able to figure it out. The few that I found through google are all fairly old, and deal with XFree86, not X.Org, so I'm somewhat hesitant to try them, although I will if I really have to.

Any help greatly appreciated.

Cheers,
 Sean

PS: If you're curious as to my suername, the first time I setup Linux on my computer about seven years ago, I was trying to think of a username ( didn't want to use my name ) and a bottle of deoderant was the first thing I saw. I've grown to used to it to change it now :)

---

### Post by prshah on 2008-08-06
Stupid suggestion: Have you tried your monitors automatic setting button? You know, the (combination of) buttons which will cause the whole screen to go crazy and then gradually settle into the perfect screen?

---

### Post by sebbss on 2008-08-06
I have the same display and i have no problems.

---

### Post by SeanHagen on 2008-08-06
[QUOTE=prshah]Stupid suggestion: Have you tried your monitors automatic setting button? You know, the (combination of) buttons which will cause the whole screen to go crazy and then gradually settle into the perfect screen?[/QUOTE]

Yeah, I've tried that, including fiddling with all of the settings. No luck :(

[QUOTE=sebbss]I have the same display and i have no problems.[/QUOTE]

Okay, can you post the screen and monitor sections of your X.Org config?

---

### Post by prshah on 2008-08-06
Another stupid suggestion: (Hey all of these worked for me once when nothing else did, in the same situation!)

Tighten the power cord where it enters into the monitor (even if you don't believe it to be loose), and then run an auto-setup once. 

If it doesn't work, then I'll shut up and never contribute anymore stupid suggestions...

(Except just one more, can't resist) Can you boot off an Ubuntu/Windows Live CD and confirm that the problem is not the monitor/graphic card itself?)

---

### Post by SeanHagen on 2008-08-12
@prshah: Tried those, no worky. When I boot into Vista ( ewww, I know ) everything looks fine, so I figure it's something with my X.Org settings.

Going to try and fiddle around some more, see if I can't figure this out.

---

### Post by SeanHagen on 2008-08-12
Gah, several days of searching, and all it took was a re-wording of my Google search to find my answer.

Apparently it was my modeline.

This was the old Modeline in xorg.conf: 

```

Modeline "1440x900" 136.0 1440 1520 1672 1904 900 903 909 934 +hsync +vsync
```

This is the new and improved Modeline:

```

Modeline "1440x900" 106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync
```

Everything is working great now. Thanks for the hints and tricks prshah :)

---

