---
title: "gnome-tweak-tool crashes after a few seconds"
date: 2013-11-08
forum: Desktop Environments
---

### Post by miceagol on 2013-11-08
Running gnome-tweak-tools, I'm able to use it for maybe 10-20 seconds before it crashes with the following error.
```

michael@totoro:~$ gnome-tweak-tool
Gtk-Message: Failed to load module "overlay-scrollbar"

(gnome-tweak-tool:20757): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 190: Element 'span' was closed, but the currently open element is 'alt'
INFO    : GSettings missing key org.gnome.nautilus.desktop (key computer-icon-visible)

(gnome-tweak-tool:20757): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 190: Element 'span' was closed, but the currently open element is 'alt'
Segmentation fault (core dumped)

```

I don't get segfault with any other programs, so I don't think it's a ram issue. Any suggestions to solutions?

---

### Post by Frogs Hair on 2013-11-08
I found and old bug report and the seg falt was due to a missing dependency . There is a newer bug report but it is for the Gnome 3 Team PPA. You could try re-installing. ```
sudo apt-get install --reinstall gnome-tweak-tool
```

---

### Post by miceagol on 2013-11-18
Tried, but didn't help. Still crashes. :-/

---

### Post by Frogs Hair on 2013-11-18
See if this bug report is applicable:  [https://bugs.launchpad.net/ubuntu-gnome/+bug/1235902](https://bugs.launchpad.net/ubuntu-gnome/+bug/1235902)

---

### Post by miceagol on 2013-11-18
Hmm, it's similar, but not the same. I don't need to trigger anything for gnome-tweak-tools to crash. I just open it, leave it for 30-40 seconds, and it crashes with the above error.

---

