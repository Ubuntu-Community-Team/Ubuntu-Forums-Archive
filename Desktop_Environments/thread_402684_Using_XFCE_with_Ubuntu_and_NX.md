---
title: "Using XFCE with Ubuntu and NX"
date: 2007-04-06
forum: Desktop Environments
---

### Post by martinveasey on 2007-04-06
I'm happily using GNOME with NX (the NoMachine flavour rather than FreeNX) and am doing fine.

I'd like to trial XFCE as an alternative (effective Xubuntu overlaid onto Ubuntu). The first stage is easy:

sudo aptitude update && sudo aptitude install xubuntu-desktop

However, I'm at a loss as to how to instruct my remote Windows client to fire up XFCE. I have seen suggestions that I should set the Desktop as Custom and use 'startxfce4' in the Settings, Run Command. I've put this both with and without the path and in each case NX errors out with Cannot Start Local X-Server.

Does anyone know what I could be doing wrong?

Many thanks,

Martin

---

### Post by magean on 2007-04-06
startxfce4 does it for me and new virtual desktop.

If you have local access can you shutdown gdm and se if startxfce4 works locally.

---

### Post by martinveasey on 2007-04-07
Many thanks, magean. My mistake was not to select "New Virtual Desktop" but instead to try to use floating window.

Change this and it worked immediately.

Best,

Martin

---

