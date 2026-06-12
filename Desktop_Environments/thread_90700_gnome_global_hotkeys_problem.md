---
title: "gnome global hotkeys problem"
date: 2005-11-15
forum: Desktop Environments
---

### Post by supenguin on 2005-11-15
I was trying to set up global hotkeys so I can pause and play and otherwise control rhythmbox no matter what program I am in.  Such as Ctrl-Alt-P to play/pause, etc. It doesn't work at all, and whatever letter I use no longer responds until I log out and log back in.

Following this thread: 
[http://www.ubuntuforums.org/showthread.php?t=68619](http://www.ubuntuforums.org/showthread.php?t=68619)
and the bugs it links to, it looks like this is actually a problem with upstream GNOME. Does anyone know of any workarounds?

Note that all default global shortcuts seem to work fine. I am running Breezy Badger with all the latest updates.

---

### Post by aysiu on 2005-11-15
The only workaround I know of is using a KDE app like AmaroK or JuK. They have pretty good support for global hotkeys (yes, even within Gnome).

---

### Post by supenguin on 2005-11-16
Thanks for the suggestion. I must say that's a bizarre workaround. It would seem like you'd have to completely switch to KDE for that to work. I'll give it a try as soon as I get a chance though.

---

### Post by aysiu on 2005-11-16
[QUOTE=supenguin]It would seem like you'd have to completely switch to KDE for that to work.[/QUOTE] No, you don't have to. Just ```
sudo apt-get install juk
``` It may have to install a few KDE libraries, but you're not installing the full KDE desktop.

---

### Post by supenguin on 2005-11-16
Thanks! That seems to work out great. I had played with amarok before, and forgot how great of an audio program it is.

---

### Post by supenguin on 2005-11-18
Anyone know if this problem is slated to be fixed in GNOME 2.14 or the next minor release of GNOME 2.12? This seems like one of those obnoxious little bugs that people won't notice, unless of course it bites them.

---

