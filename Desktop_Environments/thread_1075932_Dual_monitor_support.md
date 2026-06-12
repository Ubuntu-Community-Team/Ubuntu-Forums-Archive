---
title: "Dual monitor support"
date: 2009-02-20
forum: Desktop Environments
---

### Post by The Desert Fox on 2009-02-20
Hi Everyone

I have a single ati graphic card, the card has just one dvi port. I use a splitter to connect two monitors to it. Right now the monitors are mirrored. I have the ati driver installed and 3d rendering enabled.

I tired to extend my desktop onto the second monitor. I was partially successful. The desktop was extended, however, I get low resolution and was unable to enable special effects.

I have 2 questions:
1. How can I improve the resolution.
2. How can I enable special effects.  

I used the following to extend the desktop onto the second monitor:
sudo aticonfig --dtop=horizontal

I also tried the following and it does *not* seem to work:
I put the following at the bottom of my /etc/profile:
xrandr --output DVI-0 --mode 1280x1024
xrandr --output DVI-1 --right-of DVI-0 --mode 1280x1024

I modified my xorg.conf like so:
Section "Screen"
        Identifier "Default Screen"
        Device "Failsafe Device"
        Monitor "Failsafe Monitor"
        Defaultdepth 24
        SubSection "Display"
                Depth 24
                Virtual 2560 1024
                Modes "1280x1024@75" "1280x1024@60"
        EndSubSection
EndSection


Thanks

---

### Post by The Desert Fox on 2009-02-22
anyone?

---

### Post by The Desert Fox on 2009-02-23
I fixed this, here is how:
1. I copied back my original xorg.conf. No modifications made.
2. I used xrandr to configure dual screens.
3. I asked gnome to not override my graphics settings by -> gconf-editor->apps-> gnome-setting-daemon->plugins->xrandr->disable

I hope this  comes in handy to some of the folks out there. Also this is not my original work... I googled a lot and mixed stuff from many different blogs to make this work. Credit goes to the original authors.

---

