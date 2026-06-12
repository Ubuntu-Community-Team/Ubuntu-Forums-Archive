---
title: "[SOLVED] How to launch console to recover desktop - no panel or Alt+F2"
date: 2008-07-11
forum: Desktop Environments
---

### Post by timvn on 2008-07-11
Hi

My panel and toolbar are gone from the desktop. I uninstalled Evolution and run an update, maybe that caused it.  This problem has come up in other posts but I can't try the suggested solution of reinstalling the desktop because I can't launch the console.  

Alt-F2 doesn't work to open the console, and without a panel I can't see how else to launch it.  I was able to launch Firefox by finding the executable in /usr/bin, but I don't know what the console app executable is called or what its path is (can't see a 'terminal' or 'gnome-terminal') and couldn't find the answer via Google.  Can anyone offer help?

---

### Post by coffeecat on 2008-07-11
For the gnome-terminal, the executable is /usr/bin/gnome-terminal. Double-clicking on that brings up a terminal in my system so hopefully it will work for you.

If not, you can open a virtual console with Ctrl-Alt-F1. You have to log in again. Ctrl-Alt-F7 to get back to your desktop. Of course, you may have to restart the desktop after you've done your repairs.

Good luck.

**Edit:** Just noticed that you couldn't see gnome-terminal. Perhaps it got uninstalled somehow. Why not go to a virtual console and try sudo apt-get install gnome-terminal first?

---

### Post by timvn on 2008-07-11
Thanks, coffeecat, solved it using your suggestion -- you were a great help!

---

### Post by sayakb on 2008-07-11
Please mark the thread as solved. (Thread tools->Mark thread as solved)

---

