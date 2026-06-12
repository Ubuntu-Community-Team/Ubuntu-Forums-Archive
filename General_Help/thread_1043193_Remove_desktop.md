---
title: "Remove desktop"
date: 2009-01-18
forum: General Help
---

### Post by timboellis on 2009-01-18
I have installed Ubuntu on a small PC underpowered so now i have it all setup whats the best way to get the server to run without the desktop as it is not connected to a monitor assuming this will make it faster

---

### Post by theozzlives on 2009-01-18
Should've just installed the server version, it don't have a desktop manager.

---

### Post by timboellis on 2009-01-18
Well I could not the only version I could install was ubuntu 7.04 then update manually to 7.10 as this is a viglem MCP-L and if you look around the net there are major issues getting it working

The server version will not install on this machine

---

### Post by dragos240 on 2009-01-18
> **timboellis said:**
> I have installed Ubuntu on a small PC underpowered so now i have it all setup whats the best way to get the server to run without the desktop as it is not connected to a monitor assuming this will make it faster

Hmm, i agree with the last post, but if you want to remove the desktop, find if you have ubuntu/kubuntu/or xubuntu, if you have ubuntu unistall gnome, then X, then xorg, if you have kubuntu, unistall KDE, then unlistall X then Xorg, and if you have xubuntu, uninstall xfce, then X, then xorg. When you unistall x, you'll mostly be booted into a black terminal, from there try using aptitude to uninstall xorg, happy terminal tty'ing!

---

