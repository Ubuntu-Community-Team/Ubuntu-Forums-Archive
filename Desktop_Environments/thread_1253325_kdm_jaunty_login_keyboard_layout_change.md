---
title: "kdm jaunty login keyboard layout change"
date: 2009-08-30
forum: Desktop Environments
---

### Post by m.lp.ql.m on 2009-08-30
Using Kubuntu Jaunty 64-bit.
I type Dvorak keyboard layout, so when I was installing Jaunty on my daughter's computer, I used Dvorak as the default install layout, with the intent of switching back to Querty for her when I was done. Switching back in KDE is easy enough, but I'm unable to change the layout in the login screen. I've tried editing the /etc/X11/xorg.conf file by adding the sections as described [here]("http://ubuntufs.wordpress.com/2007/05/08/dvorak-keyboard-part1/") and [here]("http://ubuntuforums.org/showthread.php?t=31076") with no luck. Any other ideas?

---

### Post by knattlhuber on 2009-10-08
If this is still an issue, try my suggestion posted [here]("http://ubuntuforums.org/showthread.php?t=1272561").

---

### Post by marmida on 2009-10-08
Hello, fellow Dvorakian.  I found this post: 

[http://ubuntuforums.org/showthread.php?t=321326](http://ubuntuforums.org/showthread.php?t=321326)

This may be an old and dead topic, but for posterity's sake:

[LIST][*] if you selected the Dvorak layout during installation, the default keymap for the system will also be set to Dvorak.  This preference will be inherited by any window managers you install.
[*] as you've noted, you can change the settings for a KDE session, but this doesn't impact the display manager, because it assumes that the window manager's preferences are specific to a user.
[*] the settings package for the console keymap appears to be console-setup.
[/LIST]

You can re-run the initial setup and regenerate the system-wide default via: 
```
sudo dpkg-reconfigure console-setup
```

---

