---
title: "Screensaver lock up computer"
date: 2006-11-13
forum: Desktop Environments
---

### Post by ronbrooks on 2006-11-13
I was setting the Screen saver on my desktop and it is locking up the computer every time I go to to reset it my computer will lock up and every time the screen saver comes on it dose the same thing. It is set now in Molecula settings. In the the screen all I see is constructing molecules...

I want to set it back to none but it will not let me is there a way I can do it from the command line.  If this dose not work what should I do next.  New to Linux I am using Ubuntu 6.10 ](*,) 

Please help.

---

### Post by MatsyV10 on 2006-12-02
You may have already figured it out.  But all you need to do is, after rebooting drop to a terminal.  And delete the screensaver file...  this way it wont happen again by acident either.

It is located :
/usr/lib/xscreensaver/molecule

use sudo to remove...

example :
sudo rm /usr/lib/xscreensaver/molecule

---

### Post by CatKiller on 2006-12-03
Failing that, gnome-screensaver settings are stored in gconf. Alt-F2 -> gconf-editor -> /apps/gnome-screensaver will let you change the theme or mode.

Lots of people seem to have problems with molecule. I don't know why.

---

