---
title: "clock background transparency"
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by Sup3rkirby on 2007-10-17
Ok, I was accidentally messing around(bad) and I changed the background color of the clock.  Now I am using an image for my bottom panel and my clock has this ugly background.  I can't seem to set that to a transparent color.  Having KDE(Kubuntu) is supposed to make Ubuntu beautiful, so I can't stand that ugly clock right now with its non matching background.

Help please?

---

### Post by alucardromero on 2008-03-26
Easy...

Edit this file as root

```
sudo kwrite /home/<user>/.kde/share/config/clock_panelapplet_kubuntu_rc
```

Remove the values for the background color ONLY, save it, and then restart X by CTRL+ALT+BACKSPACE and you should have it as transparent.

Doesn't a lengthy response give you diarrhea? :P

I JUST now saw your post. ;)

---

