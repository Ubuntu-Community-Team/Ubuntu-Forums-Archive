---
title: "Evolution half-broken after upgrade to Jaunty"
date: 2009-05-10
forum: General Help
---

### Post by nicksukharev on 2009-05-10
I ran an upgrade from 8.10 to 9.04 yesterday and it looks like it broke Evolution. Evolution can be started but if I try to go to preferences or to open my calender, I get the following error on the console:
```
evolution: symbol lookup error: /usr/lib/libecal-1.2.so.7: undefined symbol: icalcomponent_as_ical_string_r
```
and it crashes. It looks like I got some libraries mixed up but I cannot figure out a way to do a clean reinstall. I tried the following and it did not help.
apt-get install evolution-
apt-get autoremove
apt-get clean
apt-get install evolution

---

### Post by kozlovsk on 2009-05-11
Check out this post:
[http://ubuntuforums.org/showthread.php?t=1153619](http://ubuntuforums.org/showthread.php?t=1153619)


try to backup your .evolution folder in your users home directory and then delete it, logout/login and restart Evolution, after that one more logout/login may be needed, not shure. Of course all the data will be lost, it will be in your backup though.

---

### Post by nicksukharev on 2009-05-12
apparently, I had an older version of libical in /usr/local/lib and a newer (correct) version in /usr/lib. After deleting libical* from /usr/local/lib everything is working. 
Probably a leftover from Feisty->...->Jaunty upgrading...

---

### Post by barney_1 on 2010-02-14
Thanks for that, it fixed my problem.  I had been getting crashes when clicking on the calender applet on the gnome-panel, and I couldn't even load Evolution.  Once I got rid of the older libical files that fixed it.

I used:

```
mkdir ~/libical-backup
sudo mv /usr/local/lib/libical* ~/libical-backup/.
```

Reboot and make sure everything is working.  If you have a problem you can move the files back, or delete the directory when you're certain it's fixed.

---

