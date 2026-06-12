---
title: "Gnome common files corrupt?"
date: 2007-07-31
forum: Desktop Environments
---

### Post by phstpok on 2007-07-31
Running fully patched Feisty. For some reason my Gnome environment has started crawling along, but not all the time. It takes 5 - 6 minutes for Gnome to finish loading from the login  screen, and when I open an application, such as Firefox or Nautilus file manager or Gnome terminal, they all take many minutes to boot, yet when they are up they work as normal. It's just starting the applications that takes time. And only certain applications, seemingly ones that are tied into the Gnome environment. e.g. Gnome terminal takes ages to load, but eterm and aterm load immediately.

I also have Xfce and KDE loaded, and they are fine, no slowdown at all.

There is nothing in /var/log/syslog out of the ordinary, just a keymap problem I've had for ages related to my Microsoft cordless multimedia keyboard. I've only installed 2 new applications in the past week, so I uninstalled both and did a apt-get autoclean afterwards, but that made no difference.

 I suspect there is probably one corrupt file in the Gnome common files somewhere. Would booting into KDE, uninstalling Gnome then re-installing be the way to go?

---

### Post by phstpok on 2007-08-03
I jumped in feet first and removed Gnome. I used aptitude remove gnome-common gnome-desktop-data rather than apt-get and then aptitude install gnome-desktop-environment, logged in and everything is back to normal.

---

