---
title: "Problems after installing KDE"
date: 2007-04-09
forum: Desktop Environments
---

### Post by Matt1632 on 2007-04-09
I just installed  KDE (kubuntu-desktop) and it's done a few things I don't like.  First of all, when I choose "Ubuntu" from the GRUB menu it shows the Kubuntu artwork.  I've been able to restore the Ubuntu artwork, but it only shows on shutdown.  Two, It's made all the system folders in root (bin, usr, mnt, opt, media, dev, etc.) hidden, there's a text file called .hidden that contains a list of these folders.  Can I delete .hidden to un-hide the system folders?  And, lastly, before I installed KDE I had a launcher on my GNOME desktop called hda1 and it brought up my windows partiton when I clicked on it.  The launcher is gone and I can't see any way to access my windows partition at all in GNOME.   Is there some way to fix these problems?  Edit:  Is there a way in KDE to remove launchers from the menu, but keep the launcher info in case I want to add the launcher later?

---

### Post by Matt1632 on 2007-04-09
Ok... Well I managed to fix some of my problems. I fixed the splash screen by running
```
sudo dpkg-reconfigure usplash
```
The hda1 launcher problem seemed to fix it self, would that terminal command have fixed it?
But now I'm realizing that the GUI in firefox and some other programs look much different.  Is that because I installed it while I was using GNOME or is that simply because KDE doesn't use the same GUI toolkit?

---

### Post by ComplexNumber on 2007-04-09
the GUI for firefox will always look different. that because gnome has the gtk toolkit, kde uses the qt toolkit, and firefox uses the XUL toolkit.

---

### Post by rmaus on 2007-04-10
I would also like to know how to restore the root folders to a non-hidden state.

---

