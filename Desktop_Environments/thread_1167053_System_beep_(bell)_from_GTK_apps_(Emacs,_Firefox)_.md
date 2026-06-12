---
title: "System beep (bell) from GTK apps (Emacs, Firefox) in Kubuntu"
date: 2009-05-22
forum: Desktop Environments
---

### Post by immerc on 2009-05-22
Hi all, I recently upgraded from kubuntu 8, intrepid, to 9, jaunty.  I expected some breakage, and got some.  I was able to sort most of it out, but there are a few really annoying remaining issues.

The one that's bothering me most right now is sound.  In this case, it's that GTK apps like Firefox and Emacs insist on using the "speaker beep" as a system bell, instead of using a nice sound-card based notification.  Making this much worse is a horrible design decision on the Lenovo T60 that says "if you're going to make a speaker beep and there are headphones plugged in, blow out the user's eardrums instead".

Is there a trick to getting GTK apps to use the KDE notification system, or at the very least to get them to play a sound file instead of using the system bell?  I know you can theme GTK apps to look like KDE apps, but can you theme them to sound like them too?

---

### Post by Manslen on 2009-11-01
Same issue here after upgrading to Karmic.

---

### Post by benerivo on 2009-11-01
I don't think you can get gtk apps to use the kde notification sounds, althugh you can disable the internal speaker if that helps. I think it is done by adding the line```
blacklist pcspkr
```to the end of this file```
/etc/init.d/modprobe.conf
```

---

### Post by t.rei on 2009-11-07
Is there maybe a more elegant way of doig this? Somehow gtk-apps make a sound everytime a button is pressed or anything. *grinds teeth*

I found something that might work on the kde forums:

> Solution for any one still affected:
Append to ~/.gtkrc-2.0-kde4:

gtk-enable-event-sounds=0
gtk-enable-input-feedback-sounds=0

*edit* Works - but gets overwritten if config for gtk-appearance in systemsettings is touched.

---

