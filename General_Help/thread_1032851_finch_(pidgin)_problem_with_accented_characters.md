---
title: "finch (pidgin) problem with accented characters"
date: 2009-01-06
forum: General Help
---

### Post by hellahulla on 2009-01-06
Hey.

I am using the finch frontend to the pidgin chat client and have a small problem.

Whenever I try and use the 'ö ä å Ö Ä Å' accent characters either nothing happens or with 'ö' the screen changes to what could be a debug screen and 'Ä' opens the dump page save box (normally alt-shift-d). Either way, I cannot enter them into the entry line of the page I am on.

I have my keyboard set up as Finnish in X but my language set up as English, I assume this could be part of the problem.

*locale* returns:

```
LANG=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=
```

I have tried Konsole, Gnome terminal and XTerm the same thing happens, however if I login using another tty I have not got this problem. So I assume it is X related.

Found similar issues here, but no assistance.
[http://ubuntuforums.org/showthread.php?t=498037](http://ubuntuforums.org/showthread.php?t=498037)
[http://pidgin.im/pipermail/devel/2007-July/001734.html](http://pidgin.im/pipermail/devel/2007-July/001734.html)

If there is anything else you would like to know please ask me and I'll try and get back to you soonish, thanks very much for your help.

---

### Post by plcarvalho on 2009-07-14
[http://developer.pidgin.im/wiki/Using%20Finch#Accentsarenotworkingproperly.HowcanIfixit](http://developer.pidgin.im/wiki/Using%20Finch#Accentsarenotworkingproperly.HowcanIfixit)

---

