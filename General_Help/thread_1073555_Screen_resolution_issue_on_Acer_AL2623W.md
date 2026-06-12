---
title: "Screen resolution issue on Acer AL2623W"
date: 2009-02-18
forum: General Help
---

### Post by sardamil on 2009-02-18
I recently bought a 26" screen. It usually works fine, but sometimes ubuntu won't recognize it and will configure the screen wrong. As a result part of my desktop is not shown. Any idea how I can fix this?

---

### Post by wu-stix on 2009-02-18
Have you tried System > Preferences > Screen Resolution and setting that? If you have a proprietary driver like FGLRX then you can change the screen resolution in ati catalyst.

---

### Post by sardamil on 2009-02-18
Yes, I did try that. The settings are good, but don't always work correctly. And the screen is always shown as unknown.

---

### Post by roalt on 2009-02-19
I have similar problems: I have the Acer 2623W connected to my DVI port of my IGP ATI HD3200 graphics card.

When I turn the monitor off and on again (sometimes accidentally while readjusting the monitor settings and pressing the turn-off button by accident), it goes back into 1600x1200 resolution instead of 1920x1200.

The way to solve it right now is to reset your X Server (by means of Ctrl-Alt-Backspace) and at the same time turn your monitor off and on again. If you see your gdm login window appear in the middle of the screen, the resolution is right again, otherwise repeat it until you succeed.

I think there is something wrong with the communication between the monitor and the graphics card to indicate the right resolution. I think it works allright with the D-Sub/VGA connector although I haven't tried it.

---

### Post by sardamil on 2009-02-19
Thanks, I'll try that. I've got my monitor connected to my DVI port as well, so wouldn't know about the D-Sub/VGA connector.

---

### Post by HavocXphere on 2009-02-19
[http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401](http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401)

But you didn't get that nasty band-aid hack from me :-$ and of course strictly at own risk.

---

### Post by sardamil on 2009-02-21
That sounds like a permanent solution. I just don't know all the values I should enter.

I know the resolution and the frequency. I don't know the other stuff though and can't find it in the manual either.

# 1920x1200 @ 60.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
  Modeline "1920x1200_60.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync

---

### Post by roalt on 2009-10-14
I think it's some kind of -bug- in the Acer monitor itself. However, the fastest way to get rid of the wrong resolution is to unplug the monitor's power cable and put it back in. This somehow works better than turning it off with the (middle) power button underneath the screen.

---

