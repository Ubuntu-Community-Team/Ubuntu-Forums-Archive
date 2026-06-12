---
title: "Dual AWN Docks?"
date: 2010-05-13
forum: Desktop Environments
---

### Post by peterofferman on 2010-05-13
I just installed Avant Window Navigator (AWN), downloaded a sweet theme and now kind of wish I could use two AWN docks at the same time. I searched around the forums and the internet, but found nothing. Is it impossible?

---

### Post by peterofferman on 2010-05-14
Anyone?

---

### Post by moonbeam on 2010-05-14
Yes, it can be done but it is _unsupported_ at the moment.  It cannot be done through the Preferences currently.

The relevant config keys are (you're probably using gconf so use gconf-editor):

/apps/avant-window-navigator/panels/panel_list   (number of panels).

/apps/instances/avant-window-navigator/panel-#/

Panel 1 can be configured through the preferences, panels 2+ need to be configured through the configuration backend (normally gconf).  Any changes to panels 2+ require a restart of awn.

Please do not file any bug reports wrt to multiple instances until we expose it through preferences.

---

### Post by ste.richards on 2011-03-31
> **moonbeam said:**
> Yes, it can be done but it is _unsupported_ at the moment.  It cannot be done through the Preferences currently.

The relevant config keys are (you're probably using gconf so use gconf-editor):

/apps/avant-window-navigator/panels/panel_list   (number of panels).

/apps/instances/avant-window-navigator/panel-#/

Panel 1 can be configured through the preferences, panels 2+ need to be configured through the configuration backend (normally gconf).  Any changes to panels 2+ require a restart of awn.

Please do not file any bug reports wrt to multiple instances until we expose it through preferences.

Please explain this further. panel_list doesn't exist in /apps/avant-window-navigator/panels on my version. I have AWN 0.4.1 :S

---

### Post by stinkeye on 2011-03-31
You can have multiple docks by installing from the awn-testing ppa.
It's as simple as going to awn preferences and hitting the add dock button.
[**_[COLOR="DarkRed"]http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html[/COLOR]_**]("http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html")

---

### Post by Copper Bezel on 2011-03-31
Needless plug, I guess, but I have a [how-to]("http://ubuntuforums.org/showthread.php?t=1714111") on replacing the Gnome Panel entirely with AWN. AWN Testing (avant-window-navigator-trunk) comes with support for multiple panels, a notification area, and the popular chrome-tab-looking Lucido style. The difference between AWN and AWN-testing is the difference between yet another dock app and a complete Gnome Panel alternative.

---

