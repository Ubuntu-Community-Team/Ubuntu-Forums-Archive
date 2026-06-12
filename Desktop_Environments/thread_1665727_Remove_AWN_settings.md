---
title: "Remove AWN settings?"
date: 2011-01-12
forum: Desktop Environments
---

### Post by x56sImpulse on 2011-01-12
I've been having problems with AWN's shiny switcher (the desktop switcher app for AWN).  On startup it often, but not always, appears as two identical switchers side by side.  After changing any of the preferences of the switcher it returns to normal.  After restarting the problem continues.

I have tried complete removal of the program, deleting any files or folders that look like they have anything to do with AWN settings, and restarting.  But after reinstalling it seems that all the settings stay the same.

Where exactly are AWN settings saved, specifically the settings for applets?  Any ideas?

I will try to post a screen-shot of how the applet appears when I restart later.

---

### Post by kerry_s on 2011-01-12
~/.config/awn & ~/.gconf/apps

make sure your using the latest from ppa.
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

### Post by x56sImpulse on 2011-01-12
Trying right now, thanks.

---

### Post by x56sImpulse on 2011-01-12
Ah, it looks like the settings are back to default.  I think it must have been the files in ~/.gconf/apps that I missed.  Thanks a lot.

---

### Post by x56sImpulse on 2011-01-12
... But I just restarted and the problem remains.

Here is what it looks like:
[http://i96.photobucket.com/albums/l198/SwordImpulse_2006/Screenshot-1.png](http://i96.photobucket.com/albums/l198/SwordImpulse_2006/Screenshot-1.png)

I should only have 4 windows, 2 rows, 2 columns.  It looks like 8, stretched out a bit.

I am running compiz, could that effect it somehow?

---

### Post by kerry_s on 2011-01-12
i know what your talking about now, the work spaces are controlled through gnome-settings-daemon, so what you have to do is setup the work spaces using the gnome-panel work space switcher, that will then be the same on awn.

---

### Post by x56sImpulse on 2011-01-12
Thank you very much.  I think it is fine now. :KS

---

