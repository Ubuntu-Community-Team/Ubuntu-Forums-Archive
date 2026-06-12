---
title: "Can I install Unity but keep Wayland ?"
date: 2023-04-23
forum: Desktop Environments
---

### Post by jonfisher on 2023-04-23
Can I install Unity but keep Wayland/Gnome ?

I use to be able to log out and choose to boot into Unity.  Can I install Unity and do this again, but keep Wayland/Gnome as my default environment to boot into normally?

---

### Post by monkeybrain20122 on 2023-04-23
You can install unity and keep gnome (xorg) but as far as I know you can't keep wayland as unity only works in xorg. So to install unity you have to first switch to xorg:
edit /etc/gdm3/custom.conf
and uncomment (remove # in front)
```
#WaylandEnable=false
```
then for 22.04 you have to install dbus-x11 else you can't login

(of course you can keep wayland in the sense that you could edit /etc/gdm3/custom.conf and comment out that line then reboot and login to gnome wayland, then edit it again and reboot to get into unity, but in that case you can't use lightdm to login since it works only for xorg)

---

### Post by guiverc on 2023-04-24
I'm a *lover* of having multiple desktops to my installs. My current install has Ubuntu Desktop (GNOME), Xubuntu desktop (Xfce) & what I use most Lubuntu (LXQt) which gives many many options (Ubuntu allows Xorg or Wayland session, Lubuntu allows LXQt with Lubuntu's configs; upstream LXQt or the WM openbox alone, etc)

How you switch between them will vary on the DM in use, and some allow you to default to whatever you last chose, OR have it default to a specific option.  The three systems I mentioned I have installed all default to different DM's; eg. Ubuntu Desktop (GNOME) uses gdm3, Xubuntu (Xfce) uses lightdm, & Lubuntu (LXQt) uses sddm.. When you install another DE(sktop/flavor) that uses a different DM, you get asked which you want to use.

---

