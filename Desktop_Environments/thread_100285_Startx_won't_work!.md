---
title: "Startx won't work!"
date: 2005-12-07
forum: Desktop Environments
---

### Post by CYHPT.net on 2005-12-07
Hi all,

I tried using the 'Startx' command to get to the GUI of linux. But it doesnt work. Can someone tell me how to get it worked?

Thanks

---

### Post by fourchannel on 2005-12-07
first off, linux is case sensitive so 'Startx' is not the same as 'startx' . see if that doesn't fix it. if not, then post what it says when you run it.

---

### Post by CYHPT.net on 2005-12-07
I tried both, still says "unknown command" or command cud not be found. Im using Ubuntu 5.10 Breezy. Theres 2 different setups, 1 is the server and the other is default. When I installed the server mode, I cant go to the GUI. But when I installed default, it goes straight the the GUI. I dont know why, but can u tell me why this is like this?

Thanks

---

### Post by Pablo_Escobar on 2005-12-07
Server is a type of installation that leaves you with only necessary packages.
Then you install what you want f.e. gdm, gnome, kde.
The default installation method installs already the default DE (Gnome for Ubuntu and KDE for Kubuntu)

---

### Post by Suger on 2005-12-07
As far as I know, the server version of ubuntu is what it says, a server version, so it does not include X (which is not necesarily useful on a server). So you have to apt-get X (sudo apt-get xorg-common && sudo aptget xserver-xorg should bring you were you want). If you want to use X, I think you'd be better with the normal version (you can always Ctrl+Alt+F1 to switch to console).

---

