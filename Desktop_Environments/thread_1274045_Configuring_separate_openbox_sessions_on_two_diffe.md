---
title: "Configuring separate openbox sessions on two different monitors"
date: 2009-09-24
forum: Desktop Environments
---

### Post by HamsterStyle on 2009-09-24
Hey guys,

I've just installed ubuntu 9.04 (first linux os ever for me! woo! Loved it so far!) and I'm figuring things out. I'm at the point where I'm customizing openbox in order to have an alternative and minimalist DE to the built in one. So far I'm excited about what openbox has to offer, and I'm still figuring out how things work.

So, according to the openbox documentation, openbox is well-suited to having more than instance of it running in a separate Xsession. I have two monitors, each with their own xsession. Currently I have, in the ~/.config/openbox/autostart.sh file, a line at the end that starts openbox on the right monitor:

```
# Open another openbox on the right screen.
DISPLAY=:0.1 openbox &
```So, I have two questions. 1) I hear from the openbox website I should use the ~/.xinitrc or ~/.xsession file for this. Is this the case with using Ubuntu's gdm, or is the file named something else? I currently select openbox-session from the gdm menu.

2) My other question is, how do I add configuration things upon startup to the second openbox session? The most tangible thing to think of is how do I have it automatically put one desktop image on the first OB instance, and another image on the second one, upon start up?

Any tutorials people can point me to on this, please let me know! Otherwise, I'm going to try and write something up myself once I've figured this all out :) first post!

---

### Post by HamsterStyle on 2009-09-24
Bump? Fell off page 1.

---

