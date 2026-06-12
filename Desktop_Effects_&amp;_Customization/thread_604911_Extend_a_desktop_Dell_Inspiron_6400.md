---
title: "Extend a desktop Dell Inspiron 6400"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by peterbrewer on 2007-11-06
I have a dell inspiron 6400 running gutsy with an intel video card.  I want to connect it to an external monitor and extend the desktop onto it for the purpose of presentations.  I tried changing settings within the kde manager for display and monitor and all it did was make the x server fail to boot as it said it couldn't find screens.  Any advice would be greatly appreciated.

---

### Post by smartboyathome on 2007-11-06
Were you hooked up to the screen when you booted up? I haven't had any experience with External screens, but if you were trying to connect it to a projector, I heard that most don't work with Linux.

---

### Post by peterbrewer on 2007-11-06
I can get an image on the screen without a problem if I reboot, the issue is that I want to extend the desktop across two screens.

---

### Post by peterbrewer on 2007-12-04
I have come up with a solution.  I have now created a script with the two following commands which I run when I connect an external monitor.

```
xrandr --auto
xrandr --output LVDS --left-of VGA --auto
```

---

### Post by theTailor on 2007-12-05
hey peter,
Ive been looking for a dual / extended desktop as I do lots of presentations. could you give me a little insight into you script? like, what is LVDS or any other set able parameters. I also have a inspiron 6400 with the intel graphics. 
thanks

---

### Post by peterbrewer on 2007-12-05
You can find more information here.
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#xorg.conf](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#xorg.conf)

LVDS - laptop display

I also had to add a line to my xorg.conf as the size of the extended desktop was larger than the default allowed.
```
virtual 2720x900
```

Hope this helps.

---

