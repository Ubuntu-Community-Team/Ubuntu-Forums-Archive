---
title: "running kde on a laptop, different from gnome?"
date: 2006-01-02
forum: Desktop Environments
---

### Post by nandasunu on 2006-01-02
I recently installed kde on my ubuntu gnome system. I am quite happy with it, but it seems to have less functionality with my laptop buttons than gnome. For example the volume buttons no longer work, they worked fine in gnome. Would this be because I installed the standad kde instead of kubuntu-desktop? Is there a way to set actions for my laptop buttons manually?

FYI: I am using a Compaq Presario R3000.

Thanks,
Nanda

---

### Post by shin on 2006-01-02
Download (or install by apt-get, yet I dunno in which repo they are in ubuntu) xbindkeys.

With this you can bind multimedia keys.

Put it in autostart
```
ln -s /usr/bin/xbindkeys ~/.kde/Autostart/
```

And either use graphic configuration tool xbindkeys-config or configure it manually. Create ~/.xbindkeysrc . There you put keycodes you want to bind with command to execute. To get a keycode - run "xbindkey -k". Small window will appear and when you press some key or combination of keys, check your consol.

There should be something like this:
"NoCommand"
    m:0x0 + c:236
    NoSymbol

Second line are codes you need.

Then put it in .xbindkeysrc . E.g.
"dcop kmix Mixer0 decreaseVolume 0"
    m:0x0 + c:174
    NoSymbol

To get more info - search for xbindkeys on this forum.

---

### Post by nandasunu on 2006-01-02
thanks for the help, I will try that.

---

### Post by burningbed on 2006-01-02
I got my volume and (for some apps) multimedia buttons to work by changing the keyboard in the control center (this is easier than binding the keys manually). Just look at the list of keyboards and pick the one that looks closest to your computer, if yours is not listed, try another one from Compaq or HP.

---

### Post by nandasunu on 2006-01-05
burningbed: thanks for the tip, that worked great! :D

---

