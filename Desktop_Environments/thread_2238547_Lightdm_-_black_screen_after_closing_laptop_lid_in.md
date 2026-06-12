---
title: "Lightdm - black screen after closing laptop lid in Xubuntu 14.04"
date: 2014-08-08
forum: Desktop Environments
---

### Post by Buuntu on 2014-08-08
I get a black screen every time I close my laptop lid after entering my password.  The only way to fix it is to press Ctrl + Alt + F1 and enter
```
sudo service lightdm restart
```
This is a pain, however, and it also closes all of my open applications when I run it.

I tried turning off light locker but then my computer doesn't lock at all when I close the lid, which isn't the point.  Is there anyway to retain the lock settings and not have to restart lightdm everytime I close the lid?

---

### Post by Toz on 2014-08-09
This was a bug when 14.04 first came out but has since been fixed. See [https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1303736]("https://bugs.launchpad.net/ubuntu/+source/xubuntu-default-settings/+bug/1303736"). Is your system fully updated? If it is, review post #158 in that bug report for steps to take to ensure the fix is applied properly.

The other option is to uninstall light-locker and install xscreensaver.

---

### Post by Buuntu on 2014-08-09
Thanks for the link, Toz.  My system is in fact up to date and it seemed that toggling the 'Lock on suspend' option off and on as suggested worked at first.  However, after a few times locking it I guess it reverted back to the blank screen after suspending.

For now I'll just use gnome-screensaver (prettier than xscreensaver) instead of light-locker.  I will keep an eye out for a real fix to this bug though.

---

