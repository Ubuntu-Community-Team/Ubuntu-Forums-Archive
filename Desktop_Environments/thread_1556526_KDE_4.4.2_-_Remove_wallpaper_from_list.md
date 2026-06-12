---
title: "KDE 4.4.2 - Remove wallpaper from list?"
date: 2010-08-19
forum: Desktop Environments
---

### Post by Ubunthree on 2010-08-19
I can add my own wallpapers to the list shown in the Desktop Activity Settings box, but can't find a way to remove them again. Is there a control for this somewhere else, or a config file somewhere that I could at least edit manually? I am using KDE 4.4.2, with the kubuntu-desktop package installed on top of Lucid/GNOME.

If this has been answered in another thread, please direct me there, and my apologies for the redundancy. Couldn't find an answer elsewhere, though.

Thanks.

---

### Post by Ubunthree on 2010-08-27
Never mind; some other bugs have cropped up, which I remember from previous ventures into KDEland, and which have reminded me why I don't run KDE, so I have scrubbed it from my system again.

If anyone has an answer to this, though, it may help someone else.

Thanks anyway!

---

### Post by Linuxforall on 2010-08-27
KDE rocks here plus no nonsesensical Pulse audio, to remove wallpaper, simply uninstall. KDE 4.5 here is snappier and consumes same or slightly less resources than its Gnome counterpart.

---

### Post by Ubunthree on 2010-08-29
There are a lot of things that I do like about KDE, which is why I keep trying it with every Ubuntu release. The issues that I had, in decreasing order of importance to me, were:

System started booting into Low Graphics Mode for no apparent reason, resulting in a basically unusable desktop. This happened once before, and I put so much time and effort into trying so many different things to finally fix it, that when it happened again, I didn't remember how I had fixed it the first time, and didn't feel like starting the whole process over again. This was the killer.

Every bootup gave me two dialog boxes, asking for my password in order to run some services or other which the dialogs didn't identify. Couldn't find any way to fix this either, especially without knowing which components were asking for the password.

A notification popped up with every bootup, telling me that some sound or multimedia component wasn't working. Since I scrubbed KDE, I don't remember now what that was.

Graphics performance in SuperTuxKart was jerkier, less fluid somehow, in a subtle way which was difficult to put my finger on, but threw me off. That's the only game that I had to test with, so I don't know whether it applies to others.

The wallpaper thing. I don't want to delete the images themselves; I just want to remove them from the selection list in the Desktop Activity settings. In fairness, I dabble in XFCE too, and wallpaper management there is more broken than this.

Basically KDE's little collection of annoyances ended up outweighing GNOME's. I'll probably try KDE again with some future release.

---

### Post by prosp4300 on 2011-04-08
> **Ubunthree said:**
> I can add my own wallpapers to the list shown in the Desktop Activity Settings box, but can't find a way to remove them again. Is there a control for this somewhere else, or a config file somewhere that I could at least edit manually? I am using KDE 4.4.2, with the kubuntu-desktop package installed on top of Lucid/GNOME.

If this has been answered in another thread, please direct me there, and my apologies for the redundancy. Couldn't find an answer elsewhere, though.

Thanks.

To remove user added wallpaper, you can find entry "userswallpapers" in config file: ~/.kde/share/config/plasma-desktop-appletsrc, then you can remove the wallpaper file manually.

---

