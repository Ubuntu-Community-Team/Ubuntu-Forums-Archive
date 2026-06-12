---
title: "Having issues starting Compiz"
date: 2006-09-15
forum: Desktop Environments
---

### Post by sapphiretiger on 2006-09-15
I used Automatix Bleeder to install XGL/Compiz. The install seemed to go without a flaw, until I restarted and attempted to start compiz according to the directions given in Automatix Bleeder.


[I]sapphiretiger@Watson:~$ toggle-compiz-nvidia
sapphiretiger@Watson:~$ compiz: Couldn't load plugin 'gconf'
Couldn't load settings. Reverting to defaults.

** (cgwd:5322): WARNING **: Cannot open pixmap: help

** (cgwd:5322): WARNING **: Cannot open pixmap: menu

** (cgwd:5322): WARNING **: Cannot open pixmap: shade

** (cgwd:5322): WARNING **: Cannot open pixmap: unshade

** (cgwd:5322): WARNING **: Cannot open pixmap: above

** (cgwd:5322): WARNING **: Cannot open pixmap: unabove

** (cgwd:5322): WARNING **: Cannot open pixmap: sticky

** (cgwd:5322): WARNING **: Cannot open pixmap: unsticky[/I]


___

When I use the toggle, all of my window decorations disappear, leaving just the program windows/menus. What's gone wrong, and how can I fix it?

---

### Post by seanUSXIII on 2006-09-15
Did you recently update compiz? If so, is it from Quinn's repos? (xgl.info or beerorkid?). Quinn's compiz no longer supports gconf. The startup script was standardized and can be started by typing "compiz-start" in the command line (without the quote marks). Or do a ```
sudo apt-get install compiz-manager
```. That will install compiz-manager, which can be used with quinn's compiz. This program can be used not only to start compiz, but manage themes and settings, and in the event of a compiz crash, it'll start metacity for you.

NOTE: These packages are not for compiz-vanilla

---

### Post by sapphiretiger on 2006-09-15
Aparently I didn't search hard enough.#-o 

Found a post with a similar issue that recommended I edit /usr/bin/compiz-start and place it in System > Preferences > Sessions > Startup Programs

---

