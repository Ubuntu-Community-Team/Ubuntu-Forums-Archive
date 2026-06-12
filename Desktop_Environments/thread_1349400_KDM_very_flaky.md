---
title: "KDM very flaky"
date: 2009-12-08
forum: Desktop Environments
---

### Post by grkuntzmd on 2009-12-08
I am running Kubuntu 9.10 x64 on a Dell Inspiron 1720 laptop. Since an update last week (xorg, kdm?), my machine has gotten VERY unreliable on boot. After the usual kubuntu splash screen comes up, the screen clears and shows all white dots instead of console messages. The dots change in places where text is probably appearing, but is completely unreadable. About half the time, I get a login prompt, but the other times, it seems to hang and I have to reboot (sometimes Ctrl-Alt-Del works, but other times I have to hold the power button). This morning, after I got the "dotted" screen, I pressed Alt-F1, logged in as root (I ALWAYS set the root password on a new install), and from the commandline, changed /etc/X11/default-display-manager to /usr/sbin/gdm. When I rebooted, the xubuntu splash screen came up (?!?), but I was able to log in to my usual KDE 4 session. (BTW, I have kde, gnome, and xfce all installed).

Has anyone else seen this behavior since last week?

I thought I had screwed something up, so I reinstalled Kubuntu on Sunday night (two nights ago) and then reinstalled all of the packages I had before, but the behavior returned. I am NOT using either backports or proposed updates, but I do use restricted drivers (NVidia in particular).

---

