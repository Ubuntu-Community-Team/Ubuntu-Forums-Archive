---
title: "What's happened to my other desktops?"
date: 2009-03-27
forum: Desktop Environments
---

### Post by unprinted on 2009-03-27
Suddenly, I cannot switch to them or use the programs running in them.

Although..

.. I have the desk switcher applet running in the corner of of my desktop

.. I can change how many it displays

.. I can use the programs running in desk 1 (like this browser)

.. I can see the ones running (sleeping!) in the other desks in System Monitor

.. every time I try to switch desk to use them, it says it is showing 'desk 1' and shows just a desktop background + icons, i.e. no running programs at all.

While I would prefer to be able to switch desks again, I'd be happy at the moment with a magic terminal command to redirect all the other programs to desk 1. I haven't tried restarting as some of the programs I can't get to have unsaved info I want to save.

(Gnome Metacity with Compiz 'medium' effects on 8.10 x64)

---

### Post by unprinted on 2009-03-27
Doing some more experimenting, I can also send a program to one of the other desks shown in the workspace switcher, and go to it...

... **but** it still says it's desk 1 there.

---

### Post by unprinted on 2009-03-28
I still don't know which configuration file is responsible for this, so I copied all of .gnome2 and .gconf from another user's home directory, used chown to make the contents 'mine' and restarted. 

I lost the unsaved info in the open programs, but I have the workspaces back.

---

