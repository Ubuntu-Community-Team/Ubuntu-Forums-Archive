---
title: "Window Manager failure after instaling GNOME"
date: 2005-12-17
forum: Desktop Environments
---

### Post by caic on 2005-12-17
Hello, I used synaptics to install GNOME in my Kubuntu and when I rebooted and tried to login using this desktop environment (or KDE for that matter), they both fail. When I type my user/pass and login, the screen seems to change resolution and what appears to be a bare X11 setting comes up, just a gray screen with a tiny black mouse pointer, after a few seconds it goes back to the Kubuntu login manager without showing any errors.

I don't think its an x11 problem, since I can still login using failsafe and the screen comes up with a resized terminal, kubuntu wallpaper on the background and mouse pointer showing up.

If there are no prettier ways of solving this, is there at least some way to get opt-get to show me a list of all installed packages, so I can remove one by one the ones I installed for GNOME?

Any help is appreciated.
Thanks.

---

### Post by endersshadow on 2005-12-17
You can try:
```
sudo apt-get remove ubuntu-desktop
```

---

### Post by caic on 2005-12-17
thanks for your help, but i got a message saying that package was not installed...if anyone is having the same problem, I was able to fix it by logging into failsafe mode and using "sudo dselect" to remove all of the gnome packages I had previously installed.

---

