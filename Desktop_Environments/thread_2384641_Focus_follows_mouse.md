---
title: "Focus follows mouse"
date: 2018-02-09
forum: Desktop Environments
---

### Post by VanillaMozilla on 2018-02-09
How do I configure focus follows mouse?  I'm using Ubuntu 16.04, Flashback Metacity.  I have it on another computer, but can't find it on this newly configured computer.

I tried gconf-editor, but it doesn't have any applicable settings.  There's lots of help on the Interwebs, but it's all old.  Really old.

---

### Post by VanillaMozilla on 2018-02-11
OK, gnome-tweak-tool works with 16.04, and does the job.
gsettings set org.gnome.desktop.wm.preferences focus-mode 'sloppy' is also said to work in 12.10 and later; also in 17.10.  More documentation on settings here:

[https://askubuntu.com/questions/64605/how-do-i-set-focus-follows-mouse](https://askubuntu.com/questions/64605/how-do-i-set-focus-follows-mouse)
[https://askubuntu.com/questions/978401/how-do-i-set-focus-follows-mouse-in-ubuntu-17-10](https://askubuntu.com/questions/978401/how-do-i-set-focus-follows-mouse-in-ubuntu-17-10)

Part but not all of that information is current.

---

