---
title: "[SOLVED] Keyboard remapping doesn't work under GNOME"
date: 2008-07-24
forum: Desktop Environments
---

### Post by king.pest on 2008-07-24
Hi,
I'm having a strange issue with keyboard remapping under GNOME (I'm running Ubuntu 8.04.1). I'd like to swap CapsLock and Ctrl keys, because I'm an Emacs user, and I just don't want to get my arm broken using a Thinkpad keyboard. 

I've created a custom ~/.xmodmap file, but whereas it works under Fluxbox, Openbox, FVWM and Xfce, it doesn't work under GNOME. So I tried tuning some GNOME keyboard settings, and I found that there is an option for CapsLock/Ctrl swapping, I've enabled it, restarted X windows, and it still doesn't work. 

Ideas anyone?

---

### Post by pauper on 2008-07-24
Hmm... use Vim? I kid, I kid :lolflag:

Not sure about Hardy, just tested in Gutsy under Gnome.

System--Preferences--Keyboard Preferences

Layout options.

"CapsLock key behavior" tab, select "CapsLock toggles Shift so all keys are
affected"

[color=red]And[/color]

"Ctrl key position" tab, select "Swap Ctrl and CapsLock"

And no need for ~/.xmodmap

---

### Post by king.pest on 2008-07-24
great! thanks! it works!

(and obviously I won't start using Vim:P)

---

