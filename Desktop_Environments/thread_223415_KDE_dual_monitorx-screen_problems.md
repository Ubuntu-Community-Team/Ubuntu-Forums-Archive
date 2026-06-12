---
title: "KDE dual monitor/x-screen problems"
date: 2006-07-26
forum: Desktop Environments
---

### Post by reuben on 2006-07-26
Cross posted from: [http://www.kde-forum.org/thread.php?threadid=15082](http://www.kde-forum.org/thread.php?threadid=15082)

Gnome folks; would this stuff work better in Gnome? Worth my time experimenting?
---

I have a 19"LCD monitor and a 17" CRT monitor. I've managed to get dual head working reasonably on my nvidia 6600, using seperate devices and seperate screens; i.e. each monitor has its own instance of KDE (there are two kdesktops active). This is not ideal.

Problems:

a) Settings are not shared between both KDE instances. E.g. I have different desktop backgrounds; the panel has different settings, shows different things, etc.
b) However, some settings are linked; I have my panel configured to auto-unhide when I touch the top of the screen w/ the cursor; now touching the top of either screen pops down both panels, i.e. on the CRT and on the LCD.
c) There's some sort of geometry constraint; when I drag the panel on the LCD screen, it jumps around an imaginary 1024x768 box (i.e. taking the resolution of the CRT, as opposed to the LCD.)
d) I can drag icons between the two screens (KDE prompts me with the "move here?" dialog, which is pretty cool; however, windows are stuck in the screen that I open them in.
e) Global key shortcuts only work on the LCD monitor; e.g. I have ctrl+alt+. set up to open an aterm; whether the mouse pointer is on the CRT or the LCD, the aterm always opens on the LCD screen.
f) KDM launches on the CRT; I'd far prefer it to launch on the LCD.

Here's the goal, and use case:

My LCD is center; the CRT is off to the left. Most of the time, I plan only to use the LCD, since the CRT is a different size. However, when e.g. editing video in cinelerra (which has a multiple window interface, like GIMP) it would be cool to drag some of the less important windows to the CRT, but be able to see them without switching the z-order of any windows. Or, when working on a web page, I can have quanta active on the LCD, and a browser sitting on the CRT ready to be refreshed. Etc.

It seems that this might be best accomplished by mapping each screen to a different KDE desktop.

My xorg.conf is attached. Any help here would be appreciated. It seems like some of the problems I found so far are genuine bugs that I should file, but if you know workarounds I'd like to know them first.

Thanks!
Reuben

---

### Post by CompShrink on 2006-07-26
I assume you mean mapping the screens to differnt virtual desktops, not seperate sessions like you currently do. As far as I know this cannot be done. But you can make your two monitors 1 large screen, that your single desktop spans across. I find this to work fine for the uses you describe.

I was using a PCi card along with an AGP card with Xinerama. With your current setup, just add 

Section "ServerFlags"
    Option      "Xinerama"      "true"
EndSection

and it should work. But, the better option is to use nVidia's nView.

[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors) explains how to do it,  the xorg.conf file is the same on gentoo, so I don't think there's anything you need to do differently for Ubuntu.

Tell me if you get either way working satisfactorily. And I don't think there'd be much difference in Gnome vs KDE.

---

### Post by reuben on 2006-07-26
Hello, I tried using twinview and xinerama, as that would work fine for me; however, they seem to require that the screens are the same size/resolution. Is there a way to tweak them so that they do not make this assumption?

---

### Post by philippe_carlo on 2006-07-26
I do not think that this is absolutely necessary for nvidia cards, but may be mistaking. I remember having a setup (a long while ago) with different resolutions.

---

### Post by reuben on 2006-07-26
Ah, you're right! Thanks. xinerama works fine. Twinview otoh seems to screw things up, but maybe I'm just not passing the right params to it.

---

### Post by reuben on 2006-07-26
Ah, one more tweak needed here -- how can I make the LCD monitor be the primary one, other than swapping the cables. (See my xorg.conf from my earlier post.)

---

### Post by reuben on 2006-07-26
Got it:

Section "Device"
       Identifier      "NVIDIA0"
       Driver          "nvidia"
       Option      "IgnoreEDID" "on"
**       Option      "UseDisplayDevice" "DFP"**
       Screen          0
       BusID           "PCI:1:0:0"
EndSection

Section "Device"
       Identifier      "NVIDIA1"
       Driver          "nvidia"
       Option      "IgnoreEDID" "on"
**       Option      "UseDisplayDevice" "CRT"**
       Screen          1
       BusID           "PCI:1:0:0"
EndSection

---

