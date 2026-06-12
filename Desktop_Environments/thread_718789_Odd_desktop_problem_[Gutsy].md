---
title: "Odd desktop problem [Gutsy]"
date: 2008-03-08
forum: Desktop Environments
---

### Post by denzilla on 2008-03-08
I have this weird problem: Sometimes when my gnome desktop comes up, the actual desktop is blown up to where only a section is showing. If I move my mouse toward any direction, the desktop scrolls to show the section of the desktop I just moved to. I have no idea whats causing this. It only dis this with one user account so I deleted it, created a new account and it happened in that one to. It hasn't done this on my main account, however. If I logout/login again, the problem is gone and the desktop looks as it should.

---

### Post by Arthur Archnix on 2008-03-08
Instead of loggin out, have you tried disabling compiz? When you log in, and you've got that funky screen, hit Alt+F2, then type "metacity --replace" 

If that fixes the problem then you need to delete your compiz config files, because you've probably installed CCSM and its applying the same settings to all your users.

---

### Post by denzilla on 2008-03-08
Compiz was never enabled. Using default Ubuntu desktop with no acceleration.

---

### Post by Arthur Archnix on 2008-03-08
The default Ubuntu Gutsy desktop is compiz. Anyway, I just wanted you to do that to rule out a possible problem with compiz. Consider it step one in troubleshooting.

Step two is to look at what video card you have and see if anyone is reporting strange behaviour similar to yours.
```
lspci -v
```
will spit out a bunch of information about your computer, scroll through it till you come to the video card, and then punch that into the ubuntu forums, or post it back here.

Step three would simply be to try and reconfigure your xserver. But it seems a bit premature to try that yet.

---

### Post by denzilla on 2008-03-08
Compiz is enabled by default if your card doesn't need proprietary drivers installed. I have a Ti4600 AGP card installed but never downloaded/Installed the Nvidia drivers. Could Compiz still be interfering somehow?

---

### Post by Arthur Archnix on 2008-03-08
> Compiz is enabled by default if your card doesn't need proprietary drivers installed.You're saying you're currently using metacity? That's easy to confirm; open a terminal, type gconf-editor, ctrl+F to find, type "window_manager", check search key names: look at current, and default. Do they say /usr/bin/compiz or /usr/bin/metacity?

> I have a Ti4600 AGP card installed but never downloaded/Installed the Nvidia drivers. Could Compiz still be interfering somehow?I have no idea. That's why I asked you to disable it. So we could rule it out.

Here's my second guess: If it's not compiz then it's gnome's screen magnifying tool. I'm not sure how to disable it, but uncheck anything from sessions that say "AT", which means assistive technology. Or uninstall it through synaptic. Or try and configure it through assistive technologies menu item. I can't be more specific, because I uninstall everything assistive when I setup.

---

### Post by denzilla on 2008-03-08
I check out the magnify thing when I return to work Monday. Thanks for your help :)

---

