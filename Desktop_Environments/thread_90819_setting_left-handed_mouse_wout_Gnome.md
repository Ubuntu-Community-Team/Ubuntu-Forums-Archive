---
title: "setting left-handed mouse w/out Gnome?"
date: 2005-11-15
forum: Desktop Environments
---

### Post by aok on 2005-11-15
If I don't want to use Gnome, what is the proper way to set the mouse buttons?

I read from the Debian X Window System FAQ that xmodmap should not be used with Xorg and that the only option was to set the buttons in gpm.conf but the drawback is that if there will be mutiple users on the same system with different mouse preferences, it will not be practical.

Can I use whatever tool that Gnome uses to set the mouse buttons? And if so, what is that tool?

Thanks.

---

### Post by Remmelas on 2005-11-15
hmm, i use xmodmap to map my buttons on my logitech mx310 (6 buttons + scroll), with no ill effects... couldn't hurt to give it a go, worst case scenario you have to restart x to undo the damage.

---

### Post by linkunderscore on 2005-11-15
What DE or WM are you using besides gnome? 

You could always use the gnome-settings-daemon to port gnome settings (like mouse setup) to whatever you are using.

---

### Post by aok on 2005-11-16
I've just gotten back to using Linux on a desktop after a few years hiatus so I just want to play around with different things. One thing I want to experiement with is E17 and without ALL of Gnome running. And then maybe add bits of Gnome back as I find a need (if that's possible).

I'll do some experimentation. I was just hoping someone had a better solution that the gpm.conf way for mouse. Not sure why xmodmap is now considered the wrong way though.

---

