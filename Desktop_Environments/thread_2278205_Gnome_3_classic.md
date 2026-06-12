---
title: "Gnome 3 classic??"
date: 2015-05-14
forum: Desktop Environments
---

### Post by edward1978 on 2015-05-14
I installed 15.04 & I have what looks like Unity, how can I get plain Gnome 3?

---

### Post by v3.xx on 2015-05-14
```
sudo apt-get install gnome-panel && sudo reboot
```
At the login window, click on the icon and choose 'Fallback (metacity)'

---

### Post by grahammechanical on 2015-05-14
I think we need to be clear about what we are talking about otherwise it causes confusion.

Gnome 3 Desktop Environment is the replacement of Gnome 2. Ubuntu is built on Gnome 3 but it uses the Unity user interface instead of Gnome 3 shell which is the Gnome developers replacement for Gnome 2 panel. So, in a sense Ubuntu already has plain Gnome 3.

Gnome shell classic is an extension to Gnome 3 shell that gives the look of Gnome 2 panel but we need Gnome 3 shell installed or to be running Ubuntu Gnome.

In Ubuntu 14.04 and onwards we can install gnome-session-flashback. It is in the software centre. That will give us two extra login options. Gnome Flashback (Compiz) and Gnome Flashback (Metacity). Each user interface replicates the old Gnome 2 panel look that some people think of as "classic."

Regards.

---

### Post by edward1978 on 2015-05-15
Ok, didn't mean any harm, how do I move stuff on the panels (Icons & buttons) & the app. I have open has a button (windows taskbar like) on the top panel how do I take that away??

---

### Post by deadflowr on 2015-05-15
> **edward1978 said:**
> Ok, didn't mean any harm, how do I move stuff on the panels (Icons & buttons) & the app. I have open has a button (windows taskbar like) on the top panel how do I take that away??

Depends upon what desktop you actually have running.
Did you install gnome-panel?

It's been a while but in gnome-panel/gnome-fallback, try alt + right-click on the panel.
Also try alt +super + right click, or alt +ctrl +right-click. I forget which.

If this is not gnome-panel/gnome-fallback then ignore those keybindings...

---

