---
title: "OOo file-menu pops up uncalled"
date: 2010-01-08
forum: Desktop Environments
---

### Post by ubuntwinkel on 2010-01-08
Using OOo 3.1 with Karmic.  File menu keeps popping up (as if I had done Alt-F) on its own every 20 seconds or so.  This only happens when OpenOffice has focus.  These uncalled file menu popups do not happen when other programs have focus, so it does not appear to be a keyboard issue.  And it does not appear to happen within OpenOffice when OO is unfocused.  

Hoping this sounds familiar to someone else, as searches have yielded nothing so far.

---

### Post by ubuntwinkel on 2010-01-08
It has happened before.  

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=25359](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=25359)

Sadly, no informative solution.  If 'just rebooting' was the only fix, we might as well never have left winblows.

---

### Post by ubuntwinkel on 2010-01-08
OK, with things the way they are in my system, it seems the command (to simulate user activity, from blueproximity) "gnome-screensaver-command -p" is the culprit.  Removing that from the blueproximity preferences stops the offending behavior in OpenOffice.  

Some more particulars about my system: I am running Karmic on an AMD64 with Compiz.  Version of OOo is openoffice.org-core.1:3.1.1-5ubuntu1, vanilla install via Synaptic. 

This is kind of a bug, I think, because 'solving' this requires I stop using gnome-screensaver-command.  And I don't think that is the design intention of gnome-screensaver-command.  Actually filing it as a bug against either OOo or gnome will require more self-confidence than I have at the moment.

---

### Post by Hagar Delest on 2010-01-08
You can also try to install the Sun version, perhaps it won't interfere with the other package. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by themuddler on 2010-01-08
Just experienced this on Karmic tonight while my wife was working on the laptop.  Restarting OOo made no difference.  Reboot solved the problem.  Worth filing as a bug I think.

---

