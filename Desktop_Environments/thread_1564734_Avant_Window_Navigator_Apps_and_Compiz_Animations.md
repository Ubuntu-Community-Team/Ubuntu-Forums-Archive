---
title: "Avant Window Navigator Apps and Compiz Animations"
date: 2010-08-30
forum: Desktop Environments
---

### Post by lakerssuperman on 2010-08-30
Hello,

I currently have my open/close animation set to Glide in Compiz.  However, aside from normal windows like Chrome and Nautilus, the glide effect is applied to Avants animations.  I would like the Avant animations to fade in and not use the glide effect.  I have looked at the rules and have done a little tinkering, but I haven't found the rule that would make this work.  Any help is much appreciated.

---

### Post by Helkaluin on 2010-08-31
Try the window classes 'avant-window-navigator' and 'awn-applet', set animation to 'none' for both (or whatever effect you want), and remember to place these rules in a higher priority than the usual animation rules.

---

### Post by lakerssuperman on 2010-08-31
I am not that familiar with setting compiz rules.  Should I just use the rules that are there as examples?

---

### Post by Helkaluin on 2010-08-31
By all means yes.

It's not hard, I'm sure you'll understand after fiddling with them.

---

### Post by lakerssuperman on 2010-09-07
So after some messing around I finally realized that something was just messed up on my desktop so I copied the settings from my laptop and now things that should fade, do fade.  For some reason my desktop was not behaving as it should.

---

