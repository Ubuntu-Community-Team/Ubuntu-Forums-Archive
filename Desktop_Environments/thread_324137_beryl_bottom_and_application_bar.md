---
title: "beryl bottom and application bar"
date: 2006-12-23
forum: Desktop Environments
---

### Post by arya6000 on 2006-12-23
Hey guys,

I have just installed beryl running on AIGLX witch already came with my Ubuntu 6.10, all the other things seem to be working but the bar at the top that contains the Applications, Places, etc has stayed the same, when I change themes everything changes but the two bars at the top and the bottom, in the screen shots I have seen the two bars change too, why isn't my bars changing?


Thank You

---

### Post by raul_ on 2006-12-23
You need to start gnome-settings-daemon

---

### Post by arya6000 on 2006-12-23
> **raul_ said:**
> You need to start gnome-settings-daemon

When I type gnome-settings-daemon in the terminal it says:

```
You can only run one xsettings manager at a time; exiting

```

Is there a setting that needs to be changed?

---

### Post by raul_ on 2006-12-23
Did u create a separate session for Beryl?

---

### Post by arya6000 on 2006-12-23
> **raul_ said:**
> Did u create a separate session for Beryl?

no, I just put in beryl-manager in the terminal when I want to start it, because I don't want it running at all times, since it slows down video playback sometimes.

---

### Post by raul_ on 2006-12-23
I guess that's your problem then..I use a separate session so the "gnome-settings-daemon" works for me :-k Maybe if you create a separate session it will run smoothly.

---

### Post by arya6000 on 2006-12-23
> **raul_ said:**
> I guess that's your problem then..I use a separate session so the "gnome-settings-daemon" works for me :-k Maybe if you create a separate session it will run smoothly.

I found this how-to to do it is it good?

[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/AiGLX)

---

### Post by raul_ on 2006-12-23
That's the one i used :)

---

### Post by arya6000 on 2006-12-23
:confused:  I made another session and logged in with it, but the top and bottom menu still looks the same, even when I change the themes :( any ideas?

---

### Post by astoltz on 2006-12-23
What are you expecting to happen?  Beryl / Emerald do not change anything in the gnome panels that I am aware of. Even under a "regular" gnome session, the themes do not change the panels (application bar).  You can change the appearance by right clicking in the panel and from there click on properties.

---

### Post by arya6000 on 2006-12-23
Thanks, I got it

---

