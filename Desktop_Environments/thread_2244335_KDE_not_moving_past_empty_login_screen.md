---
title: "KDE not moving past empty login screen"
date: 2014-09-15
forum: Desktop Environments
---

### Post by ltjimmy on 2014-09-15
Hey Folks,

new to Ubuntu (and Linux) and loving it so far.  However, upon installing the KDE desktop environment to check it out this morning and then attempting to restart and log in with user/passsword,  it's just sitting on an empty (what I'm guessing is the default) KDE background wallpaper. No icons, applications or anything.

  Mouse cursor seems to move around so it's not hanging or crashing,  but nothing seems to load up allowing me to interface with the environment.
Also, now when I attempt to restart and load back into the Unity or Gnome desktop it still defaults to this new black KDE background.

Any tips on how one might go about fixing this?  Thanks!

---

### Post by xc3RnbFO8P on 2014-09-16
You can rename your .kde folder ( .kde-bak)in your home folder hidden, Ctrl - H or show hidden  files) and restart.

---

### Post by ltjimmy on 2014-09-16
Thanks for the feedback.  I'd give this a try,  except it won't actually allow me to boot into any of the desktop environments. Instead hanging on the background of the default KDE login page.  Regardless of which desktop environment I choose to enter.

---

### Post by Erik1984 on 2014-09-16
You can probably log in without a desktop by using one of the TTYs. For example CTRL + ALT + F1 for TTY1. Now you have a command line without a graphical desktop (X-server). Here you can also rename your .kde folder :
```
mv ~/.kde ~/.kde_bak
```

---

### Post by Bucky Ball on 2014-09-16
Welcome. As Erik1984 has explained. You can also boot to a live desktop from the install media and do it that way if you're more comfortable with a graphical interface.

---

### Post by ltjimmy on 2014-09-19
Thanks everyone. This is the direction I'll take.  Cheers.

---

