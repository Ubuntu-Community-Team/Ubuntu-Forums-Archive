---
title: "Multiple displays+NVidia driver-&gt; video tearing artefact"
date: 2010-12-02
forum: Desktop Environments
---

### Post by fa2k on 2010-12-02
Hi, 

when I watch video, the picture is split somewhere in the middle of the screen, so that it looks discontinuous and ugly. The position of this "tearing" changes, and it's mostly visible in video scenes with lots of horizontal motion. 

I'm using the NVidia driver, and I'm using an external monitor with a laptop. The problem does not appear on the laptop screen. I fixed the problem in Gnome by turning on desktop effects (Compiz) and setting the refresh rate to 60 Hz in Compiz Config Settings Manager. I also had to turn on "sync to VBlank" for XVideo in the nvidia-settings application. 

Is there a similar trick in KDE that I can use to make the video look OK?

Thanks,
Marius

---

### Post by inobe on 2010-12-02
[http://kubuntuguide.org/Lucid#Configure_Dual_Monitors_with_nVidia](http://kubuntuguide.org/Lucid#Configure_Dual_Monitors_with_nVidia)

from here

[http://kubuntuguide.org/Lucid](http://kubuntuguide.org/Lucid)

---

### Post by fa2k on 2010-12-02
Thanks inobe, that's actually a different problem, the "toggle display" button doesn't work. I found an awesome program called "disper" that lets me switch between displays. (I used to have it bound to Ctrl-F7 and Ctrl-F9 in Gnome, but those are used for something in KDE). 

I still have the problem , but thanks a lot for the link, looks very useful for many things


Marius

---

### Post by inobe on 2010-12-02
so you change sessions between kde and gnome and the bound settings don't apply to kde ?

Fn+F8 is a known vga toggle key code.....

i don't have an external, i googled screen toggling.

---

### Post by fa2k on 2010-12-03
I found that the problem is fixed by

1) disabling desktop effects, 
2) enabling "Sync to VBlank" under OpenGL in nvidia-settings
3) watching videos in VLC media player using OpenGL mode

I don't seem to have this problem with flash web videos (even with desktop effects installed), so the VLC solution is pretty satisfactory.

---

