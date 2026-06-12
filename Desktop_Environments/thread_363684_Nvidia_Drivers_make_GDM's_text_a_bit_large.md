---
title: "Nvidia Drivers make GDM's text a bit large"
date: 2007-02-17
forum: Desktop Environments
---

### Post by Dylnuge on 2007-02-17
Hello,

I recently installed the actual Nvidia drivers. The first thing I noticed is how well all the graphics ran with them. The second thing I noticed is that the text in GDM was larger.

If anyone knows anything about this problem, help would be appreciated.

Thanks

---

### Post by taurus on 2007-02-17
You can change the resolution in /etc/X11/xorg.conf.  

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by kerry_s on 2007-02-17
Add a option in xorg.conf for your dpi in the monitor section.->
    Option         "DPI" "96 x 96"

adjust according to you monitor, like 100x100 or 120 or lower 75
size depends on what resolution you use i have mine on 96 for 1280x1024.
You have to restart X to see effects(ctrl+alt+backspace)

---

### Post by Dylnuge on 2007-02-17
The problem only exists with GDM, and not with Gnome, KDE, Fluxbox, or E17.

I will still try this and see if it helps.

Thanks.

---

### Post by kerry_s on 2007-02-18
Here's a great site to calculate what DPI would work best-> [http://www.raydreams.com/prog/dpi.aspx](http://www.raydreams.com/prog/dpi.aspx)

I moved my dpi to 109x109 like it recommended and it looks right now. Yes DPI controls GDM and the whole system, you can compensate for it in the DE by changing the fonts size so you don't really notice the DPI is wrong.

---

