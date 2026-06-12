---
title: "PenguinTV problems..."
date: 2006-01-07
forum: Desktop Environments
---

### Post by GameGod on 2006-01-07
Anyone here us [PenguinTV]("http://penguintv.sourceforge.net/")?

It looks like a really cool/useful app, but I can't get it to work. I'm pretty sure I have all the installed packages and stuff, but when I run it, the window shows up and then freezes...

If I run from the terminal, I get the following output:
```
alb@Jupiter:~$ PenguinTV
/usr/lib/python2.4/site-packages/penguintv/penguintv.py:895: GtkWarning: gtk_window_resize: assertion `width > 0' failed
  self.app_window.resize(self.conf.get_int('/apps/penguintv/app_window_size_x'),self.conf.get_int('/apps/penguintv/app_window_size_y'))
Traceback (most recent call last):
  File "/usr/bin/PenguinTV", line 35, in ?
    penguintv.main()
  File "/usr/lib/python2.4/site-packages/penguintv/penguintv.py", line 1643, in main
    app.Show()
  File "/usr/lib/python2.4/site-packages/penguintv/penguintv.py", line 851, in Show
    self.load_settings()
  File "/usr/lib/python2.4/site-packages/penguintv/penguintv.py", line 917, in load_settings
    self.window_preferences.set_player_cmdline(val)
  File "/usr/lib/python2.4/site-packages/penguintv/PreferencesDialog.py", line 54, in set_player_cmdline
    if player_cmdline.startswith(inlist):
AttributeError: 'NoneType' object has no attribute 'startswith'
```

Anyone see what's wrong here?

Thanks!

---

### Post by Omnios on 2006-01-07
Not that I can help out but this is a totaly amaazing developement for Linux. Id rate it aa 9.5 on the rictor scale of  Linux advancement

---

### Post by ywwg on 2006-01-07
Hi, I wrote PenguinTV.

I don't know why this happens, but if you log out of GNOME and log back in it fixes the problem.  What's happening is that my gconf settings are being installed, but GNOME isn't seeing them correctly.

edit:  I just made a 1.01 release that should work around this problem.

---

### Post by GameGod on 2006-01-07
That fixed it, thanks a lot! :)

---

### Post by lynx2cross on 2006-01-08
What exactly is PenguinTV ?

---

### Post by Zerocool10482 on 2006-01-13
PenguinTV is not just another RSS feed reader. It is designed from the ground up to work seamlessly with podcasts and video blogs, allowing you to easily enjoy the audio, music, and video published around the web in RSS format.
User Interface

Until now, the only solutions for listening to podcasts on Linux have been clunky apps and unreliable bash scripts. Many solutions require the user to browse file directories named by date to find media files. With the large amount of information in podcasts and videos, a user needs help to keep track of everything.

[http://penguintv.sourceforge.net/](http://penguintv.sourceforge.net/)

---

### Post by Omnios on 2007-07-09
Visited the PenguinTV homepage today and they have debs.

[Stable Version 3.0 Released]("http://penguintv.sourceforge.net/#download")

[http://penguintv.sourceforge.net/](http://penguintv.sourceforge.net/)

**[[B]Download stable version 3.0 for Ubuntu Feisty**]("http://downloads.sourceforge.net/penguintv/PenguinTV-3.0-ubuntu7.04.i386.deb")[/B]


**[[B]Download stable version 3.0 for Ubuntu Dapper**]("http://downloads.sourceforge.net/penguintv/PenguinTV-3.0-ubuntu6.06.i386.deb")[/B]

---

