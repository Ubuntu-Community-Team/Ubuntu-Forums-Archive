---
title: "Gnome panel multi-desktop problem"
date: 2012-12-13
forum: Desktop Environments
---

### Post by msknight on 2012-12-13
Hi Folks,

12.10 64 bit version.
HD Radion card installed.

sudo apt-get install gnome-panel
...and the classic gnome is chosen on log-in.

However, on enabling multiple desktops and switching between them, the gnome panel bars vanish, never to return until a reboot.

Anyone have any ideas please?

---

### Post by ibjsb4 on 2012-12-13
That is an odd problem.  Are you fully updated?  Next time it happens try in terminal:

```
killall gnome-panel
```

That should at least save you from rebooting until you figure it out.

---

### Post by msknight on 2012-12-14
Thanks for that. It will save a reboot, but I'm stuck on one virtual desktop until I get it figured. I must have missed a package, but I can't figure out what.

---

### Post by ibjsb4 on 2012-12-14
> **msknight said:**
> Thanks for that. It will save a reboot, but I'm stuck on one virtual desktop until I get it figured. I must have missed a package, but I can't figure out what.

Try resetting your dot config file.

home /.config/gnome-panel  and  maybe change it to /gnome-panel.old; log out for changes to take place.

[Package list]("http://packages.ubuntu.com/quantal/gnome-panel")

---

### Post by msknight on 2012-12-16
Hi,

Doesn't look like there is a resolution. The "gnome-panel" handles multi-desktop in a different way, so the best option I have is to install "gnome-shell" instead. Not as light but I did notice a lightgdm option in there somewhere so there does seem to be an option to handle it.

Many thanks.

---

### Post by msknight on 2012-12-16
I don't know what happened, but it seems to have sorted itself.

Removing the gnome-panel system and just relying on the gnome-shell just ended up in some bastardisation of unity which was absolutely awful.

I had to re-install gnome-panel, but the applet was still out of whack with the four screens that Ubuntu had installed.

However, after removing and re-installing the workspace switcher, although it initially looked like it did before, it has somehow managed to pick up the 2x2 pattern and apparently works, even though, when I go in to the preferences, it thinks I'm only using 1 workspace.

If I manage to repeat what I did successfully, I'll let you know ... but at the moment, this is a bit of a bananas way of doing things!

---

### Post by stinkeye on 2012-12-16
This thread may be helpful to your understanding.
[**_http://ubuntuforums.org/showthread.php?p=12373597#post12373597_**]("http://ubuntuforums.org/showthread.php?p=12373597#post12373597")

---

