---
title: "Xgl + Dual Monitor"
date: 2006-06-05
forum: Desktop Environments
---

### Post by djvishnu on 2006-06-05
I have an ati 9600pro card with xgl set up workin perfectly. What i want to do now is to to use two monitors in a dualhead setup. I have never done this before, and I am in need of some guidence. What i want is a setup with the screens side by side, but not as the same desktop (so that maximized windows only fill one screen). Out of what i have read **Twinview** does this. (?) I have also read that xgl breaks twinview, however when googling "xgl twinview" this is the first hit:

[http://lists.freedesktop.org/archives/xorg/2006-May/015460.html](http://lists.freedesktop.org/archives/xorg/2006-May/015460.html)

(he says he's got it working perfectly)

I need some hints on how the dualhead can be set up. (and weather it actually is possible with xgl atm)

Thank you

---

### Post by ktulu1115 on 2006-06-06
I believe Twinview is what you don't want actually.  At least this is what I gathered from the NVIDIA docs (I know you have an ATI).  I didn't think XGL didn't work with Twinview, or any dual displays at all....  maybe this changed, or I'm incorrect.  Last time I tried XGL, it worked on my system, but only on one display - maybe it's due to the way I have it configured:

I setup my xorg.conf as seperate X displays....  no Twinview, no Xinerama, nothing.  I like having full X sessions on each display (panels on each) plus the ability to run each display at different resolution (I have two different Dell LCDs).

I'd check out the NVIDIA doc page on configuring multiple X displays - even though you have an ATI, most of the info on that page will still apply, just got to change accordingly: [http://download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-p.html](http://download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-p.html)

---

### Post by Jason_25 on 2006-06-06
Xgl does not break twinview, it has nothing to do with it.  For more information, visit the compiz forums.

---

### Post by leohart on 2006-06-08
Any one has any information on how to get Twinview and Xgl working? Turning off one monitor really makes me feel a little down.:???:

---

### Post by denjin on 2006-06-08
Have you tried it yet (to the OP)?  I know you probably want to look at xinerama, as that is the ServerLayout option that lets you do the two screens and drag windows between them, but when you maximise, they stay on their current screen.  What do you mean by twinview?  The twinview option I tend to think of is sorta like mergedfb, but for nvidia.

MergedFB is supposed to work, but then you just get the large single display, but split between the two.  Googling says that xinerama+xGL=nogo now as far as I can tell.  Sounds like you did a bit of research on this already, though.

---

### Post by djvishnu on 2006-06-09
Well, im getting mixed messages on this one. People say it should be impossible, but on the compiz.net forums there are quite a few that has it working. It may be I just havent tried hard enough yet :)


Another "myth" i want confirmed (or busted, doh) is whether the fglrx driver is capable of resolutions greater than 2048xX? if not, my dual screen dreams go down the toilet, I cant risk be seen with 1024 res on my screens :)

---

### Post by viz_e on 2006-06-13
It should be possible to run Xgl on two screens with xinerama. However, if I enable xinerama, I loose the 3D support and Xgl with it... I really don't know why... :-({|=

---

### Post by jrei on 2006-06-14
[QUOTE=ktulu1115]I believe Twinview is what you don't want actually.  At least this is what I gathered from the NVIDIA docs (I know you have an ATI).  I didn't think XGL didn't work with Twinview, or any dual displays at all....  maybe this changed, or I'm incorrect.  Last time I tried XGL, it worked on my system, but only on one display - maybe it's due to the way I have it configured:

I setup my xorg.conf as seperate X displays....  no Twinview, no Xinerama, nothing.  I like having full X sessions on each display (panels on each) plus the ability to run each display at different resolution (I have two different Dell LCDs).
[/QUOTE]

That is what I use for Xorg. But if I use XGL the second screen does not contain anything, except a plain X. I tried to display some programs on it but I get an access denied.

If you have any idea whats the problem please tell. :)

Greetings, Jörn

---

### Post by RawMustard on 2006-06-15
I'm running xgl-compiz with twinview enabled and it works fine.  Well I don't experience any more bugs than anyone else :)  I'm running a 7800 GTX, don't know if it works with an ATI card.

---

### Post by ktulu1115 on 2006-06-19
Has anyone gotten Xgl working with dual displays but *without* twinview or xinerama?  I have my system configured as two seperate X servers, one on each display.

---

### Post by madfitz on 2006-07-12
I have an Nvidia GeForce 6200 on an AMD64 system with twinview working perfectly (3200x1200 res), however I have not attempted to get xgl to work on it. It took forever to find a good comprehensive xorg.conf file that would get the two monitors to work correctly together and I fear breaking it.

In addition I have a 32bit system I installed ubuntu 6.06 and got xgl to work on a cheep Nvidia 64Meg card (only 1 monitor) with amazingly fast xgl effects. The problem I came across was with having to run GDM to get to my user's GUI. I usually remove the GDM startup as I prefer a command-line until I want the GUI overhead.

If I did not run GDM first the windows decorations (borders, maximize/minimize/close/move-handles) were not available and the windows all overlapped in the upper left corner on top of the gnome panel, not allowing access to the logout. Very aggravating If I started GDM first the windows decorations would be back and I could use the xgl eye candy effects rather amazingly fast.

Another problem I saw with xgl was the dialog boxes without a minimize/maximize/close buttons could not be moved, they always appeared right in the center of the display sometimes covering something I needed to see to answer it correctly.

I guess I wish to know if anyone else has been successful in getting twinview with xgl working w/o starting GDM. until then I guess I'll have the ability but not the guts to risk it.

I'll try on my test box with an ATI card though that system is just a 32bit. Though I'm not sure what the difference is between a 64bit xgl and a 32bit xgl. Someone had said the 64bit version was broken? I'm guessing that's probably old news.

Anyway if anyone has any answers to these questions I would love to hear from you.

---

### Post by Anduu on 2006-07-13
FYI Twinview is for NVidia cards not ATI....I too have a Radeon 9600 and messed around trying to get XGL running on the big desktop.No joy.

I have not looked into Xinemara yet...one day.

---

### Post by sonoma on 2006-07-19
> **Anduu said:**
> FYI Twinview is for NVidia cards not ATI....I too have a Radeon 9600 and messed around trying to get XGL running on the big desktop.No joy.

I have not looked into Xinemara yet...one day.

Me too - no second screen while in XGL.
ATI 9600, when in XGL/compiz, the second monitor has an X cursor and is mostly black. Dual screen two monitor setup works great in normal Gnome sessions.

Have been searching ubuntuforums and trying, but still, I just haven't seen ANYONE spill the trick to get a dual monitor setup working in XGL/compiz, if it's even possible yet. I have heard that we are waiting for "extensions?" to be released by Nvidia and Ati, but that was mentioned in March as being close to happening.

---

### Post by Excentrik on 2006-07-21
> **sonoma said:**
> Me too - no second screen while in XGL.
ATI 9600, when in XGL/compiz, the second monitor has an X cursor and is mostly black. Dual screen two monitor setup works great in normal Gnome sessions.

Have been searching ubuntuforums and trying, but still, I just haven't seen ANYONE spill the trick to get a dual monitor setup working in XGL/compiz, if it's even possible yet. I have heard that we are waiting for "extensions?" to be released by Nvidia and Ati, but that was mentioned in March as being close to happening.

With ATI (fglrx driver) it is not possible to run resolutions higher than 2048x768 in Xgl (as someone already mencioned):
[http://www.compiz.net/viewtopic.php?id=692]("http://www.compiz.net/viewtopic.php?id=692")

There is more information scattered in the compiz forum and in the net about this problem.
As far as I know, there is no date to when this resolution problem will be solved.

Best regards,
Nicolau

---

### Post by darkstar62 on 2006-07-22
I've got two GeForce cards in my system -- an older GeForce 3 Ti AGP and an FX5500 PCI with dual output, setup in X with multihead, but not with TwinView or Xinerama (i.e. they're all separate screens, :0.0, :0.1, :0.2).  I've managed to get Xgl/Compiz working across all three, with Gnome working and everything, but it's a bit tricky.

Using one of the various guides in these forums (don't remember which off hand), I set up an Xgl session through GDM.  This gives me Compiz on my primary head only.  In my gnome session, I added an entry for a script I wrote that starts up Xgl/Compiz on my primary screen (as part of the HOWTO), but additionally calls another script that starts Xgl on the other two screens and starts the gnome panel and Nautilus there.  The scripts I use are:

compiz.sh -- Starts compiz on the primary head
```

#!/bin/bash
unset XLIB_SKIP_ARGB_VISUALS
cgwd &
compiz --replace gconf &

# Call another script to load up Gnome
# onto the other two screens.
exec $HOME/bin/compiz-multihead.sh

```

compiz-multihead.sh -- Starts compiz and Gnome on the other heads
```

#!/bin/bash
unset XLIB_SKIP_ARGB_VISUALS

# Setup Xgl on the other two screens
DISPLAY=:0.1
Xgl -br -dpi 85 -fullscreen :2 -ac -accel glx:pbuffer -accel xv:fbo -lines -vbo -xvfilter nearest &

DISPLAY=:0.2
Xgl -br -dpi 85 -fullscreen :3 -ac -accel glx:pbuffer -accel xv:fbo -lines -vbo -xvfilter nearest &


# Setup the rightmost screen
DISPLAY=:2
cgwd &
compiz gconf & sleep 1
gnome-settings-daemon & sleep 5
gnome-panel --disable-sm & sleep 5
nautilus -n & sleep 5

# Setup the leftmost screen
DISPLAY=:3
cgwd &
compiz gconf & sleep 1
gnome-settings-daemon & sleep 5
gnome-panel --disable-sm & sleep 5
nautilus -n

```

Obviously, change these for your setup.  My primary screen is :0.0, with its corresponding Xgl running as :1.  The other two screens, :0.1 and :0.2, have their Xgl as :2 and :3 respectively.  The result of this is a fully-functional gnome desktop across all three screens, complete with desktop and panels.

But, there's a gotcha: Using this method, you'll get the same panel and desktop configuration on all screens -- you can't customize the panels and desktop icons on a per-screen basis like you can normally.  For me this isn't really a problem, but it's something to consider.  Also, it takes a HUGE amount of memory to do this, as you're essentially logging into Gnome three times (or as many times as you have screens), so if you have a lot of panel applets, expect a huge amount of memory usage.  After I boot, I get about 450mb of RAM used, whereas I used to have around 250mb with a standard setup.  For me, it's not an issue -- I have 1gb of RAM -- but be warned, it's resource hungry.

Also, replace cgwd with gnome-window-decorator if you're using that one.  I generally find that the new cgwd decorator that came out recently is a lot faster than the original gnome-window-decorator.

Good luck
- Cory

---

### Post by RawMustard on 2006-07-22
If you have an nvidia card capable of twinview, xgl/compiz works just fine in twinview.  Don't know about ATI's stuff sorry.

It does have a few silly quirks with window placement and firefox seems to have the odd display problem infrequently, but other than that, the speed increase over metacity is worth it IMHO!

First get twinview working properly and then install xgl/compiz and all should be just fine :)

---

### Post by n00bian on 2006-10-29
#!/bin/sh

DISPLAY=:0.0
Xgl :1 -fullscreen -audit 0 -ac -br -accel glx:pbuffer -accel xv:fbo &

DISPLAY=:0.1
Xgl :2 -fullscreen -audit 0 -ac -br -accel glx:pbuffer -accel xv:fbo &

exec gnome-session
---------------------------------------

I have an nvidia chipset on my laptop.
The above file is my startxgl.sh.  I currently have running two separate monitors in xorg.conf:

"Screen0" LeftOf "Screen1"

So non-twinview and non-xinerama and I am running Gnome.  Gnome loads correctly on both displays, however Xglx loads as a window on both displays... NOT fullscreen like it would if startxgl was configured for one display.  Can anyone advise?


-EDIT: the Xglx windows that are open have X cursors and are blank.

---

### Post by 00arthuryu on 2007-04-14
same problem :(
only a 'x' cursor on second screen running on xgl with non xinema with ati X1950
help :(

---

