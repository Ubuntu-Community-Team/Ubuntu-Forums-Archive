---
title: "E1505 power management"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by sr20ve on 2007-06-27
I've set my power management to "blank screen" when lid is closed, for both AC and battery, and it doesn't seem to be working. I can still see that my display is on when the lid is closed. I'm running Feisty. Any help is appreciated.

---

### Post by speaker219 on 2007-06-27
Does it happen in Windows? It should work, I used to have that laptop running Feisty and that worked fine. It could be one of the actual sensors that senses when the lid is closed.

---

### Post by sr20ve on 2007-06-27
> **speaker219 said:**
> Does it happen in Windows? It should work, I used to have that laptop running Feisty and that worked fine. It could be one of the actual sensors that senses when the lid is closed.

I recently wiped windows off my laptop and it worked fine before. When I close the lid, it does lock my session. I'm using my TV as an external display, so I'd like for my laptop display to turn off when I close the lid.

---

### Post by Paul S on 2007-06-27
It probably depends which video card you have and which driver you're using.  I had the ATI X1400 fglrx, and could not get the panel to blank off when closing the lid.  But, with fglrx is the "aticonfig --enable-monitors=tv" command that will shut it off and just leave the tv on.  Now, I have the nvidia video card with the nvidia driver, and it's the same problem. But, I can use the nvidia-settings program to select which screen to run. Maybe the intel video will do it .. is that what you had?

Anyway, if you're going to use the tv only for a while and nothing else works, you can always use the "sledge hammer approach" .. just edit your /etc/X11/xorg.conf to specify the tv, and hit ctl-alt-backspace to restart X to enable the new settings.

HTH,

---

### Post by highlighter on 2007-06-27
I just figured out that if I have Beryl running, my power setting will not work. I f I turn off Beryl then I can closed my lid and it goes to sleep...

You may have the same kind of issue...

---

