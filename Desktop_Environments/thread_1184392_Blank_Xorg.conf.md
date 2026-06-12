---
title: "Blank Xorg.conf???"
date: 2009-06-11
forum: Desktop Environments
---

### Post by Daeboy on 2009-06-11
So I ran a clean install of jaunty recently and (almost) everything worked great! Even my LCDtv which I used to have to write modelines for in xorg.conf worked with no modification whatsoever -- or so I thought.

I was happily watching some movies... then decided [since this is a laptop] that I wanted to go out on the porch with it. Obviously I can't use the LCDtv as a monitor. So I shutdown the laptop and unhooked it from the tv. I booted it back up... black screen.

Uh oh. "What have I done now," I thought. So I rebooted once more to make sure - still the same. Just a black screen with my mouse. Next time I booted into terminal to manually edit this faulty xorg.conf. Well - there is one, but - it's BLANK. No data in it.

I thought it was interesting and tried logging on as another user. It worked. Their desktop looked perfectly fine. So I'm assuming there's some hidden file/folder in my specific home directory that would make it act... well... different? :P Any ideas?

---

### Post by Lampi on 2009-06-11
I guess Xorg.conf is supposed to be empty with Jaunty clean install - most of the stuff that used to be in there is getting auto probed these days, what's left is in ~/.config ~/.kde (depending on your GUI in use) spread over a few xml files.

This doesn't mean you can't use a xorg.conf anymore - you'd have to set one up on your own with the basic Section entries. Xorg will always parse your xorg.conf first, then follows the stuff in your home directory.

---

### Post by Daeboy on 2009-06-13
I went into my ~/.config folder and found nothing indicating resolutions, monitors, etc. I just don't understand why the LCDtv worked fine but when I rebooted my screen was black. :P I could do it again, but I'd risk going through a lot of trouble like I did the first time.

[Very, VERY long story short (not to mention stupid of me) I ended up with no alternative but to delete my user and re-add it - losing all of my files]

I think what I'm going to do is write a modeline for the LCDtv in my xorg.conf and comment it out when I'm not using the LCDtv. That's not really a "solution" per se, but it's the best thing I can come up with for now.

Gnome is my GUI, by the way. Is there any file -specifically- in the .config folder that deals with overall "monitor performance"? I found the menus and things like that - but like I said - nothing having to do with actual monitor behaviour or resolutions.

Thanks for the help and sorry for being a pain. :P

---

### Post by gradinaruvasile on 2009-06-13
type
sudo dpkg-reconfigure -phigh xserver-xorg
in a terminal

then 

sudo nvidia-settings

in case u have nvidia card

---

### Post by asmoore82 on 2009-06-13
> **gradinaruvasile said:**
> type
sudo dpkg-reconfigure -phigh xserver-xorg
in a terminal

This is depreciated and should not be used anymore -
it actually does nothing on 9.04 but replace xorg.conf
with a fresh empty one that is mostly comments:
```
**asmoore@ubuntu-lenovo:~$** wc /etc/X11/xorg.conf 
  34  160 1038 /etc/X11/xorg.conf
**asmoore@ubuntu-lenovo:~$** sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090613023826
**asmoore@ubuntu-lenovo:~$** wc /etc/X11/xorg.conf 
  33  160 1037 /etc/X11/xorg.conf
**asmoore@ubuntu-lenovo:~$** grep '^#' /etc/X11/xorg.conf | wc
     19     134     783
```

xorg.conf can still be used to override automagic settings such as
which extensions to load or which video driver to use;
but it should no longer be used to set modelines or resolutions -
this is all done on-thy-fly now through XRandR.

you can simply run `xrandr` with no options to see a list of what devices are
connected and what resolutions they support.

I have a metacity keyboard shortcut Alt+F7 that runs:
```
xrandr --auto
```
which automatically enables/disables hot-plugged displays.

you don't even need Xorg.conf to do over-sized virtual screens anymore -
the highest my laptop panel can go is 1280x800 but I can run 1280x1280
in a "scrolling" display window like this:
```
xrandr --fb 1280x1280 --output LVDS --mode 1280x800 --panning 1280x1280
```

and to return to normal:
```
xrandr --fb 1280x800 --output LVDS --mode 1280x800
```

the standard gnome screen resolution settings dialog "Display" which I'll admit used
to be useless is actually quite good now - it's *almost* as powerful as `xrandr`

Long story short, for your LCDtv, you may be able to just need to
open "Display" and use the "Detect Monitors" button - if it doesn't
"just work" yet it will in the not-too-distant future.

---

### Post by Daeboy on 2009-06-13
Wow, thanks a lot! Oddly enough I got a different result this time 'round (as I was dumb enough to hook it back up to the LCDtv to see if I got the same results). Before shutting down the laptop and unplugging the LCDtv I decided to be smart this time and run the gnome-settings-properties program.

I tinkered around with the screens for a moment - fiddled with the resolution a bit - and it asked me if I wanted to save it to a configuration file of sorts (said it was recommended) - so I complied. What this actually did was turn my blank xorg.conf into a xorg.conf for the LCDtv.

So now - without any modelines, mind you - my xorg.conf is specifically geared towards the LCDtv and I've commented it out until I use it next. :) However, having read your post I'll definitely do more research of my own on the subject. Thank you very much for all of the helpful info.

---

