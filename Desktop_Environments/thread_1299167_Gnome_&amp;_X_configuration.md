---
title: "Gnome &amp; X configuration"
date: 2009-10-23
forum: Desktop Environments
---

### Post by rfritz on 2009-10-23
Gnome seems to override /etc/X11/xorg.conf somewhere. I'm looking at an xorg.confg file that references configured this and configured that, and no clues as to where the configuration takes place. Can anyone point me in the right direction?

---

### Post by Giblet5 on 2009-10-23
/etc/X11/xorg.conf is used but if you're using the nvidia driver, most of the stuff is automated.

The easiest way to tweak appearance is to use System/Administration/NVIDIA Display Settings to get it exactly the way you want (WYSIWYG), then save the settings to xorg.conf in your home directory.

Edit that to do what you need with a tablet, magic mouse, and keyboard.

Copy the old file to backup: ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Move the new one in: ```
sudo mv $HOME/xorg.conf /etc/X11/xorg.conf
sudo chown root:root /etc/X11/xorg.conf
sudo chmod 644 /etc/X11/xorg.conf
```

Now restart the X server: ```
sudo /etc/init.d/gdm restart
```

Confirm that the new settings are in effect.

---

### Post by rfritz on 2009-10-26
If I owned an NVidia card, that would probably be a useful answer--thanks.  Unfortunately, it's an ATI card, and I had to beg just to get the system, so no hope of changing it.  It looks like I may have to upgrade the drivers.  I've been using Hardy Heron, but perhaps the easiest thing to do is to upgrade to Jaunty.

---

