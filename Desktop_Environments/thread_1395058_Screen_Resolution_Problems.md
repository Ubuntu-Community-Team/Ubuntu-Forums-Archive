---
title: "Screen Resolution Problems"
date: 2010-01-31
forum: Desktop Environments
---

### Post by Snaps55 on 2010-01-31
Hi,

I am a new user to Ubuntu and appear to be having a few problems with screen resolution.

I have up to date drivers for my NVidia gefore 9600GT and am running from HDMI into a Panasonic 32" TV.

The available resolutions do not match what I need to fit my screen, was just wondering if there was anyway of making my own resolution on Ubuntu.

1920 x 1080 is good width but cant see any toolbars as they go off the screen so I am currently using 1600x1024 which has the perfect height but cuts about an inch and a half off of each side.

Thanks.

---

### Post by realzippy on 2010-01-31
if 1920 x 1080 is your TV's native resolution,you should set this in nvidia-settings also...and check the TV menue for some autosize option...

---

### Post by darshana on 2010-01-31
What is the refresh rate you have set, it has a big effect on refresh rate also. Try setting 
same rate in your other Operating System.

---

### Post by Snaps55 on 2010-01-31
Thanks, But my t.v does not have any useful options.
Ubuntu is now the only operating system I use so refresh rates should not be an issue.

---

### Post by chewearn on 2010-01-31
Find out the native resolution of the TV's LCD panel from the TV user's manual.  This usually located in the technical specification section.  Then, there would be no doubt about the best resolution to use.

Possibly there might also be a "overscan" option in the TV settings.  Turn that off to get the best result.

---

### Post by efflandt on 2010-01-31
Not sure if nVidia proprietary drivers are different, but the usual X tools for determining and testing different resolutions are **xrandr** and **cvt**.

Although, I would have expected HDMI to automatically be perfect, because it should communicate more about its capabilities to the video source than VGA.  When I DVI connected an older 1280x720 HDTV while my PC was suspended from previously using 1280x1024 monitor, it initially woke in its previous mode (displayed stretched).  But just logging out of gnome and back in, it switched to the 1280x720 perfect widescreen native mode of the HDTV.

It was different when I VGA connected my laptop to what was supposedly a 1366x768 HDTV.  Trying to match up the laptop display and that, it defaulted to a 1024x768 mode, and the 1280x720 (720p) mode it offered was blown way off of the HDTV screen (so overscanned that the TV could not shrink it).  From looking at /var/log/Xorg.0.log, I determined that a 1360x765_60 mode was optimum.  So I used cvt to determine a modeline for that, and xrandr to test it and turn off the laptop display.  But since I am not always connected to that display, I wrote a script with the xrandr commands and a launcher on the desktop to run it when double clicked.

---

### Post by Snaps55 on 2010-02-01
Thanks, i looked into that, optimum is 1920 x 1080 according to Xorg.
However it is still overstretched across my whole screen when i use 1920 x 1080.

Is there any way to input my own resolution?

Any help is appreciated.
Thanks Again.

---

### Post by Snaps55 on 2010-02-01
Ok i seem to have fluked a fix!

Thanks for all of the help!

---

