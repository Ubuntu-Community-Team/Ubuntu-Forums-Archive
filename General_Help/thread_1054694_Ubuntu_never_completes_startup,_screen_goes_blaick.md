---
title: "Ubuntu never completes startup, screen goes blaick"
date: 2009-01-29
forum: General Help
---

### Post by bakaeigo on 2009-01-29
Today the screen froze while the screensaver was on, and the mouse and keyboard were non-responsive. I shut it off, but when I started it up again, ubuntu went about halfway through startup but the screen went blank (moniter went into sleep mode) and the mouse and keyboard did nothing, so I can't log on. Now the only thing that I can do is press Ctrl+Alt+Backspace at which point the screen comes out of sleep mode for a few seconds only to go right back into it.

How can I fix this?:(

---

### Post by bluefox815 on 2009-01-29
Well, obviously the keyboard can do something, even if it isn't much.  Have you tried CTRL+ALT+F1 through CTRL+ALT+F7?  You could also try booting to a LIVE CD to see if it's a software or hardware error, or try to backup whatever information you need with the LIVE run before you reformat and install Linux again.

---

### Post by bakaeigo on 2009-01-30
Ctrl+Alt+F1 works and I can log into my system with the terminal, what next?

---

### Post by bakaeigo on 2009-01-30
*bump*

:( I still can't get into X, using "startx" fails. What do I do?

---

### Post by bakaeigo on 2009-01-30
Update:

I used Grub to boot into an earlier kernel version (2.6.24-16), and now I can at least get into X. However, I have to manually boot into that version every time from grub, and it uses low graphics mode without compiz as it doesn't seem to be working with the nvidia drivers, so this seems like a temporary fix. How should I go about getting everything to work again?

Thanks for any help

---

### Post by bakaeigo on 2009-01-31
Update:

I uninstalled the nvidia drivers and re-installed them through synaptic in an older kernel version. Now when I boot into the most recent kernel version, I can log in through the GUI, but it freezes usually right after loading my desktop background. Also, during boot a lot of the words in the messages are mis-spelled, for example "Wbuntw" and "Ma}r" instead of "Ubuntu" and "make".

0.0 This just seems to be getting worse and worse.
Can anyone offer any help? I really don't want to have to re-install.

---

