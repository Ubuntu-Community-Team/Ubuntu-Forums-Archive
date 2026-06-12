---
title: "[SOLVED] unreadable small font in xubuntu"
date: 2007-11-25
forum: Desktop Environments
---

### Post by mojoman on 2007-11-25
Hi,

I've  installed Xubuntu 7.10 (64-bit) and all fonts are unreadable (a pixel or so high I guess). This is in the login screen as well as in xfce4. I've tried the following hacks so far:

In the file ~/.config/xfce4/Xft.xrdb I've added the following line:
```

Xft.dpi: 96
```

I logged out, making sure that the save settings was unchecked when I logged out. No difference.

In the xorg.conf I added the following line (in the "nv" section)
```

Option   "DPI" "96 x 96"
```
I also tried this with the nvida driver enabled, which I *think* I managed to install from the cli but I'm not sure. No good on either alternative.

Also, in the gdm.conf file I tried editing a line, adding the dpi 96 so it looked like so:
```

command=/usr/bin/X -br -audit 0 -dpi 96
```
It didn't make any difference.

I also tried the autogenerating a new xorg.conf and using an old xorg.conf from my feisty installation but neither works.

Now, as everything is unreadable I can't edit anything from within xfce4. I could open a terminal and punch in a command but I can't read it or read the output, though I can start it in safe mode or go to console login from gdm. The only way I can choose console login is because I know that is the last option in the menu, and when I log out of xfce4 I know that the checkbar is 'save settings' but I can't actually read these things.

I'm at a loss here. Any ideas, anyone?

Cheers
/mojoman

---

### Post by elvinatom on 2007-11-27
i got a similar problem, i got ubuntu 7.10 i386 text-system installed running blackbox.  when i use gdm login manager the fonts are about 2-3 pixel high - impossible to read.  i found no fix so far (other than logging in without gdm and then starting x)

---

### Post by elvinatom on 2007-11-27
ok, my issue is solved:

It appears that the font size is calculated relative to the actual monitor size in milimeters.  just add under the "Monitor" section in the "/etc/X11/xorg.conf" the following line:

DisplaySize 339 212

and it's all good.

---

### Post by mojoman on 2007-11-27
Thanks, that did it for me too.

/mojoman

---

