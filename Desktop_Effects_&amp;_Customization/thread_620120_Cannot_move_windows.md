---
title: "Cannot move windows"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by lomion on 2007-11-22
Hi!

I've installed compiz-fusion on Kubuntu 7.10. Everything has been good for a few days, but suddenly I'm not able to move my windows anymore by mouse! :confused: This is really strange. I deleted all my configurations and re-configured compiz. but after logout, again it happened. 

I'm confused...

---

### Post by RSingh on 2007-11-22
Maybe your "move window" plugin is disabled. Install the compiz config manager if not already, by the command:

```
sudo aptitude install compizconfig-settings-manager
```

then go to System-->Preferences-->Advanced Desktop Effect Settings.

Scroll down to the the Window Management plugin area (at the bottom), and look for the "Move Window" Plugin, make sure there is a tick next to it, if not then activate it by ticking it.

Hopefully this should fix the problem.

---

### Post by thecoolcat on 2007-11-22
I have the same problem too. (And this happened after checking/unchecking some of the options in compiz fusion.)
My "Move Window" has a check mark. Still I'm unable to move my wondow.

Also, I don't see the buttons for Iconize, Minimize/Maximize and Close on the top right hand corner of each application/xterm I open. Can someone point me to what I missed?
Thanks.

---

### Post by thecoolcat on 2007-11-22
Hah! Here's the check mark needed in "Advanced Desktop Effects Settings":
Effects -> Window Decorations is checked.

This brought back my window borders.

---

### Post by rune0077 on 2007-11-22
Try holding down the Alt-key, then click anywhere inside the window and moving the mouse while holding down both Alt and left mouse. It might work. It's a stupid way to do it, but at least, if it works, that means Move Window is functioning.

---

### Post by lomion on 2007-11-22
I have enabled checked the mentioned plugins. Nothing changed. I had to purge remove compiz and reconfigured it from the beginning and things are normal again. But this is not a solution!!!

---

### Post by Jongleur on 2008-03-23
I'm having exactly the same problems.
How do I remove compiz?

---

### Post by Jongleur on 2008-03-23
Sorry - dumb question.
I've now done it and everything's back to normal

---

