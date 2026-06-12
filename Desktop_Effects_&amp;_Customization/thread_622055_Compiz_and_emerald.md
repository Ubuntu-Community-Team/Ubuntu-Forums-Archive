---
title: "Compiz and emerald"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by mavix on 2007-11-24
When I enable desktop effects in Ubuntu, the borders and title bars of the windows disapear. So after a bit of searching I read somewhere that I can use emerald to fix it. I downloaded emerald, but I have no idea how to use. If I select a theme in emerald, nothing happens.
Please help!

---

### Post by madsmeg on 2007-11-24
Have you tried getting emerald themes? getting emerald alone will not do anything
```

sudo apt-get emerald-themes

```
i think that is it

---

### Post by Forlong on 2007-11-24
> **madsmeg said:**
> Have you tried getting emerald themes? getting emerald alone will not do anything
That's not correct and emerald-themes is not even in Gutsy's repos.

mavix, please tell us more about your system, particularly what version of Ubuntu and graphics card & driver.

---

### Post by mavix on 2007-11-24
I downloaded emerald-themes, but I still got the same problem. Nothing happens when I select a theme.

---

### Post by mavix on 2007-11-24
My computer is running Ubuntu 7.10, and the latest restricted nvidia drivers. My graphics card is a geforce 440 mx, my computer is a celeron 2.6ghz, with 256mb ram.

---

### Post by ST.x on 2007-11-24
you need to put emerald --replace in the window decorations section of compizconfig and reboot

---

### Post by Forlong on 2007-11-24
> **mavix said:**
> My computer is running Ubuntu 7.10, and the latest restricted nvidia drivers. My graphics card is a geforce 440 mx, my computer is a celeron 2.6ghz, with 256mb ram.
Run this in a terminal:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Restart X and try again.

---

### Post by mavix on 2007-11-24
It worked! Thanks for the help.
I also have another problem, everytime I start up, ubuntu resets my screens resolution to larger than the screen can handle. Is there any way I can change this?

---

### Post by Forlong on 2007-11-24
I recommend starting an own thread for that problem and posting your /etc/X11/xorg.conf there.


P.S. please mark this thread as solved. Thank you.

---

