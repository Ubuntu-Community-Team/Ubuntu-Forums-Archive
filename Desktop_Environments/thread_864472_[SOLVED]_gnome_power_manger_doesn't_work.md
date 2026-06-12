---
title: "[SOLVED] gnome power manger doesn't work"
date: 2008-07-19
forum: Desktop Environments
---

### Post by jimmy the saint on 2008-07-19
I cannot seem to find a way to make the settings in gnome-power-manager take effect.  No matter what options are checked, there is no power management.  This issue results in a lot of threads here, for example search for "xubuntu suspend password" for example.  That brings up several threads about not being able to enable a password prompt upon resuming from suspend.  I have tried installing gconf-editor as well, but nothing seems to be able to make the power manager settings make a difference.  It runs at startup.  I hope that someone can help me troubleshoot this.  This is one of the biggest issues that I have seen with Xubuntu and it needs to be fixed.


thanks

JTS

---

### Post by jimmy the saint on 2008-08-02
[http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)

solution there

---

### Post by tetsuo29 on 2008-09-06
I would like to confirm that the how-to at [http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557) fixes this problem. I'm quoting it here for convenience:

> 
HOW: Applications>settings manager> click on Autostarted apps button.
click add. give it a name, a description and for command type
"gnome-screensaver". click ok and then CTRL-ALT-BACKSPACE. log back in and your power settings will actually work, including suspend password, screensaver and whatever screen settings you have selected.

It's only been about 30 min. since I followed those directions, but my screen has yet to blank.

---

### Post by jimmy the saint on 2008-09-10
did you confirm that gnome-screensaver is running?

applications > system > system monitor 

and look at the processes.  If it is running, check your power settings. If you are using a laptop, it may be an unrelated problem related to that model.

---

