---
title: "Mozilla window over Gnome panels"
date: 2008-08-01
forum: Desktop Environments
---

### Post by DMurray on 2008-08-01
Hi, everybody.

Today I just opened the Mozilla browser and it started in like a full screen mode.
I mean, the browser window covers both the top and bottom panels of the Gnome window manager. And the top bar of mozilla is hidden, so I can't minimize, maximize, resize and close with the buttons.
There is nothing to control this behaviour in the preferences, it just happened all of a sudden.
If I don't have another application to switch to with ALT+TAB, it is not possible to access the Gnome menus.
I restarted X, restarted the computer, but nothing fixed so far.
Any1 knows WTH is that?
System is Ubuntu 8.04 x86.

Thanks in advance

---

### Post by tuxxy on 2008-08-01
Press the F11 key

---

### Post by DMurray on 2008-08-01
Hi Tuxxy.
At first I thought it was a matter of the F11 key, which toggles full screen mode, but it is not the case.
I may have described it in a confuse way. The program top bar is not shown, and the panels either, but it was not caused by F11.
What can I say?
BTW, hitting F11 twice brings it back to normal. Kinda weird.

---

### Post by bazza on 2008-08-02
I have had this problem since I installed the latest  offered updates for Ubuntu 8.04 - around an hour ago.
F11 works around it.

On my xubuntu 8.04 system Firefox bombs out when selecting tools/downloads or tools/add-ons. No Back/Forward navigation buttons. Also, I have lost all my application launchers in the desktop control bar. Exit does not offer shutdown/restart options anymore it just exits the desktop manager. Oh yes, I was requested to do dpkg --configure -a for that upgrade.

---

### Post by Glen Darby on 2008-08-12
Hi,

Exactly the same here, thought it was just me for a while....
Not found a fix, but in order for me to get it back I put the browser into full screen mode, then take it out of full screen mode. Never fixes it fully as I have still got the problem when I open a browser again.

As someone said earlier, it seems to have happened recently after an update, but don't know which one has caused it.

Hope someone finds a fix soon as it is really really anoying.

Glen.

---

### Post by finer recliner on 2008-08-12
have any of you tried reseting your firefox config file by renaming your .firefox/.mozilla (i forget what its called now)file?

by renaming your config file, and then starting firefox, a new one with default settings will be created for you. this may remove the bug you are seeing. 

if it doesnt fix anything, delete the new config that was created, and rename your old one back to the original name to restore your settings

---

### Post by ajozz13 on 2009-06-03
I had the same issue, To fix this you need to manually resize your firefox frame, close firefox and the next time you load the program it will start up with the min.max.close buttons visible.  I believe the cause of this is that some websites that open pop ups expand the size of your firefox frame, and upon closing the browser the browser "remembers" the size of the window last used.
Perhaps there is already a modifiable setting in the the browser config utilty to prevent this or the hard-code the initial setting for the browser....

---

