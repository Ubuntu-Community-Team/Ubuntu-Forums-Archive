---
title: "Remote desktop gnome ubuntu 22.04"
date: 2022-10-19
forum: Desktop Environments
---

### Post by paozaf2 on 2022-10-19
Hi all,
I installed ubuntu 22.04.1 on my workstation (gnome).
I want to connect multiple users at the same time via remote desktop.
I tried RD and VNC but they don't work as I wish.

I think RD is not working because of X-wayland problem.
VNC is working but only when the user is already physically logged in.

I didn't try x2go because I read it's not working on gnome.

Any suggestion?

Thanks a lot.

---

### Post by TheFu on 2022-10-19
Don't use Gnome3+. You probably didn't want to see that, but there it is.

x2go provides a virtual desktop for the local user and view-only for others.  But it doesn't work with DEs that want direct access to the GPU hardware like Gnome v3 and v4 or KDE plasma.  Use XFCE, LXQt, Mate, Cinnamon, or any of the other non-GPU connected DEs. Also, many lite window-managers work perfectly, like openbox  or fvwm.

Is the DE really important?  Not to most people.  Gnome is doing lots of non-standard things the last few years, like letting applications control window borders.  Sigh.  Blasphemy! The window-manager controls window boarders, placement, and can kill an application. It is part of the standards for how a window manager should behave.

The only way I've read that Gnome3 and Gnome4 remote desktops work is with Wayland and between other Gnome3+ workstations.  That's pretty limiting, IMHO.  I could be wrong. Won't be the first time.
[https://wiki.gnome.org/Projects/Mutter/RemoteDesktop](https://wiki.gnome.org/Projects/Mutter/RemoteDesktop)  That link has a bug reporting system link.

---

### Post by ActionParsnip on 2022-10-20
What are you wanting to do on the remote system? There may be a sleeker solution to what you want to achieve

---

### Post by ActionParsnip on 2022-10-20
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)

---

### Post by paozaf2 on 2022-10-21
Thanks for the suggestion.
I installed xfce (before that I removed gnome) and I'm successfully using x2go.

Thanks a lot!

---

