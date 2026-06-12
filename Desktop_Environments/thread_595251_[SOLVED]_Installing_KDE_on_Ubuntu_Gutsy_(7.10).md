---
title: "[SOLVED] Installing KDE on Ubuntu Gutsy (7.10)"
date: 2007-10-28
forum: Desktop Environments
---

### Post by hal8000 on 2007-10-28
Without changing to kubuntu I would like to add kde to the list of window managers in Gutsy.

Gnome 2.10 is default, I have used synaptic to add kde 3.5.8 packages, however no entry has been made in gdm.

I went to /etc/gdm/xsessions

and manually created an entry for kde.desktop

Name=KDE
Exec=/usr/bin/startkde

My entry appears but kde would not start. I searched the filesystem and there is no startkde on my
Ubuntu. Either I've missed a package or this is not the way to start kde.

Thanks in advance for a solution.

---

### Post by aysiu on 2007-10-28
What KDE packages did you add through Synaptic?

---

### Post by TeaSwigger on 2007-10-28
kde.desktop is in /usr/share/xsessions here, but like aysiu said, what did you install? kde-desktop?

---

### Post by hal8000 on 2007-10-29
sorry duplicate reply

---

### Post by hal8000 on 2007-10-29
I installed via synaptic from the kde desktop environment section.

All my packages were 4:3.5.8-0Ubuntu0-2,  I just checked and noticed kdebase was not installed? Installed using synaptic and kde 4.3.5.8 is ruuning happily now.

Thanks guys for your help

---

