---
title: "need help with TV OUT through VGA (ATI Radeon 9000)"
date: 2008-12-09
forum: General Help
---

### Post by megamania on 2008-12-09
I am trying to get my older computer to work with my TV (scart/rca cable).

It has an ATI Radeon 9000 Sapphire with DVI, VGA and S-Video output.

I bought a VGA-to-TV cable on ebay (my TV has no S-video input). It was very cheap so I decided to give it a try. In order to be on the safe side, I clean-installed ubuntu 8.10 because I read somewhere it has some out-of-the-box support for Ati TV-out.

But... if I just connect the computer to the TV, as soon as it starts booting I get a rolling screen (not even the BIOS screen is steady), but I obviously can't work on the computer to try to set it up properly.
On the other hand, if I connect the DVI output to my computer monitor AND the VGA output to the TV, only the DVI output appears to be active: 

xrandr says:
```

ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1600 x 1200
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   60.0     60.0*
   1600x1024      60.2 
   1440x900       59.9 
   1280x960       60.0     60.0 
   1360x768       59.8 
   1152x864       60.0 
   1024x768       60.0 
   800x600        60.3 
   640x480        60.0     59.9 
   720x400        70.1 
S-video disconnected (normal left inverted right x axis y axis)

```
If I try **xrandr -d vga-0** I get a "can't open display vga-0" error.

I tried to check my xorg.conf file, my to my surprise it was substantially empty.

Is there anything I can try to enable the tv output? I've been going through a lot of research but I'm not able to make any progress.

I'd love to have my old ubuntubox converted to a multimedia machine, but until I change my TV with a newer one I need to bear with TV-out!

---

### Post by megamania on 2008-12-10
Anybody please?

---

### Post by guga31bb on 2009-03-28
Bump because I have a similar problem...

---

### Post by mrreality13 on 2009-03-28
any one any ideas?

---

### Post by KeyserSoze93 on 2009-03-28
I was just trying this with my laptop's ATI card earlier, and I followed several guides with no joy.

With S-video to RCA jack, it says s-video disconnected.

I shall bookmark this thread, and hope you get it working...

---

### Post by guga31bb on 2009-03-28
Yeah mine also said s-video is disconnected. I tried with VGA and also didn't have much success. Hopefully someone smart will come help us =)

---

### Post by shohart on 2009-04-01
damn stuff... got the same trouble. ATI xpress200, running on open drivers. VGA-0 disconnected. should say it works with propriete drivers, but with it most of fullscreen apps do not work priperly (the screen is blinking)... i suppose it to be a bug...((((

---

### Post by shohart on 2009-04-02
yeah, guys, it`s definitly a bug! dunno for sure, but it seems that i`ve solve this problem in some way. 
the first is that it is impossible to make xrandr see that TV is connected. F*ck it. We`ll go another way.
my tv has primary resolution 1280x768, so i needed to have this resolution in xrandr`s list:
```
xrandr --newmode "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
```
then, i added this mode to the VGA-0 and to LVDS outputs 
```
xrandr --addmode VGA-0 1280x768 --addmode LVDS 1280x768
```
after all this stuff we can make the final step - enable VGA-0 and disable LVDS:
```
xrandr --output LVDS --mode 1280x768 --output VGA-0 --mode 1280x768
xrandr --output LVDS --off
```

i switch LVDS output mode to 1280x768 to avoid distortion on the VGA-0 output.
and after all this stuff i`ve made a script for all this commands and placed a lunch button with it on the ubuntu pannel.

oh by the way. to make all the things back - just reload x server or, enter the following:
```
xrandr --output LVDS --mode 1280x800 --output VGA-0 --off
```
take care, guys

---

