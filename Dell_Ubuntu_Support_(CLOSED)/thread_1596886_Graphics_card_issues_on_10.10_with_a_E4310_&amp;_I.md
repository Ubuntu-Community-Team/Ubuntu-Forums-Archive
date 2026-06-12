---
title: "Graphics card issues on 10.10 with a E4310 &amp; Intel HD"
date: 2010-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ShakataGaNai on 2010-10-14
I've got a Dell Latitude E4310 running Ubuntu 10.10 Desktop x64.  It has an Intel HD graphics card.  I've got two fairly major issues with it and I CANNOT seem to find the answer.  Myself and a co-worker have been tinkering with it for the last couple of hours without much headway.

Problem #1 - If you plug in an external display and enable it - it instantly becomes the "default".  By that I mean all the menu bars (whatever the ubuntu equivalent of the windows Start Menu is called) move over to the external display.  This is NOT what I want, and excessively annoying - especially because if I unplug without turning off the display - I cannot get to the system menu to turn it off.

Problem #2 - If I enable the external, disable it and then re-enable it again - it hard locks up my machine (not just X, everything - from what I can tell).

Any help would be appreciated.

---

### Post by robegs on 2010-11-11
I have de same problem with the E-port plus.

- Starting the laptop in the dock. When I unplug my laptop from the dock the internal screen don't work and if I plug it again screens, keyboard or mouse don't work. I may reboot it by touching the on button.

- Starting the laptop out of the dock. When I plug it in the dock the external mouse and keyboard works, but the external screens not.

I try to user scripts like:

```

#! /bin/sh
# Xsetup - run as root before the login dialog appears

#xconsole -geometry 480x130-0-0 -notify -verbose -fn fixed -exitOnFail -file /dev/xconsole &

if xrandr -q | grep -q  "VGA1 connected"; then
 if xrandr -q | grep -q  "HDMI1 connected"; then
    xrandr --output VGA1 --off
    xrandr --output HDMI1 --off
    xrandr --output DP1 --off
    xrandr --output VGA1 --mode 1280x1024 --primary
    xrandr --output HDMI1 --mode 1280x1024 --left-of VGA1
  fi
else
    xrandr --output DP1 --mode 1366x768
fi

```

but it don't fix my problems.

---

