---
title: "Xubuntu 15 - At login screen, onscreen keyboard doesn't work. Solutions?"
date: 2015-07-01
forum: Desktop Environments
---

### Post by halfnote52 on 2015-07-01
Hi everyone!

I've just been tinkering with installing Vivid Vervet Xubuntu on an Acer Aspire 11 SW5-171 - you know, the shmexy little tablet/laptop hybrids? 

I've got the thing working BEAUTIFULLY except I've yet to play with getting screen rotation going (not a big deal to me) and the actual problem at hand;  namely the fact that at the login screen, the onscreen keyboard doesn't work.

Oh, I can call it up, but when I type on it, nothing happens. I've plugged in a mouse, and that doesn't do the trick either.  Only a real keyboard will do.  I'd like to be able to slip this thing into and out of suspend mode while carrying it around without snapping it back onto its dock every time I log in/out of it. 


By the way, it looks like the login's password bar loses focus when I start clicking/tapping on the onscreen virtual keyboard, so I don't know if this is an issue with window focus, or permissions for the keyboard to give input to the window, or what. I'm hoping you guys can help.

Cheers!

-Duffy W.

P.S. I DID install Cinnamon desktop on this, in addition to XFCE, but I don't think that's the issue. I'll try to replicate the issue with the stock live boot and see what I see.

---

### Post by flocculant on 2015-07-02
It works here (but I have 15.10 dev version) 

Run this in a terminal (or manually check) 

```
grep onboard /etc/lightdm/lightdm-gtk-greeter.conf
```

Does it return

```
# keyboard = command to launch on-screen keyboard (e.g. onboard)
keyboard=onboard
```

I do have vague memories of having a similar issue when testing 15.04.

---

### Post by halfnote52 on 2015-07-03
Yup! It was a greeter issue. It's fixed.  Of course, same thing happens with the vncviewer, so I'm going to have to find a version that accepts onscreen keyboard input.

---

