---
title: "easy way to change dual screens resolution in xfce?"
date: 2009-01-31
forum: Desktop Environments
---

### Post by cr0ntab on 2009-01-31
Gnome has this nifty app named gnome-display-properties that detects your monitors and allows you to move them around and change the resolution of each monitor independently from the other. Since Gnome doesn't seem to support separate wallpapers for each screen, I switched to Xfce.

Unfortunately, Xfce has no equivalent that I know of, and gnome-display-properties doesn't have any effect when run from Xfce. :|

Is there any way to independently change the resolution of each monitor in Xfce that doesn't involve modifying xorg.conf? Relevant info: Radeon 9700 Pro with radeon driver, and 24" + 22" screens.

Thanks

---

### Post by cr0ntab on 2009-01-31
Update: xrandr does what I want, but the changes aren't permanent. :\

```
xrandr --output VGA-0 --off
xrandr --output DVI-0 --mode 1920x1200
xrandr --output VGA-0 --auto --right-of DVI-0 --pos 1920x0
```

Those commands will make my desktop as I want it, but the bad thing about it not being permanent (besides being horribly inconvenient) is that Xfce is started without the knowledge that I have two screens, and all the dual monitor preferences are absent.

---

### Post by cr0ntab on 2009-01-31
I just discovered this: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Putting those xrandr commands into ~/.xprofile and making it executable (chmod +x ~/.xprofile) worked for me.

---

### Post by gunit888 on 2011-09-14
This is exactly what I needed!  I used your technique of putting the xrandr commands in a script and it worked perfectly.  I just had to use xrandr to get my own personal settings (I'm using a laptop screen with an external monitor, so the output labels were a bit different).  I'm running Xubuntu 11.04 on a pretty new Asus laptop and this worked flawless, thanks for saving me some time!

---

