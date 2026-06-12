---
title: "Unexpected Changes after Upgrade"
date: 2005-04-15
forum: Desktop Environments
---

### Post by oars on 2005-04-15
Howdy!

I have been running Warty since this fall and loved it.  Today I upgraded to Hoary and there are a few things missing/changed.

1.  My fonts in menus and such are now very ugly.
2.  I no longer have a wireless monitor as a gnome applet??
3.  I also no longer have Inbox Monitor availible as a panel applet.
4.  **Biggest Problem**  Synaptic seems to have disappeared.


Hmm . . . . If anyone has solutions to these problems, let me know.

Thanks!

---

### Post by Leif on 2005-04-16
1. System->Preferences->Fonts. Go wild.

2 & 3. No idea, I don't use them

4. sudo apt-get install synaptic. Sometimes it gets left behind.

---

### Post by ubuntu_demon on 2005-04-16
you should also do : 

$sudo apt-get ubuntu-base ubuntu-desktop

after the dist-upgrade.This will install synaptic and other missing things (if any).

regarding fonts go see :

[http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)

and

[http://ubuntuforums.org/showthread.php?t=23426](http://ubuntuforums.org/showthread.php?t=23426)

For microsoft true type fonts for the web do this :
$sudo apt-get install msttcorefonts

For missing fonts from msttcorefonts and multimedia programs and other stuff you might want to run ubuntu-geeks script :

[http://ubuntuforums.org/showthread.php?t=22646](http://ubuntuforums.org/showthread.php?t=22646)

---

