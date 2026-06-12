---
title: "Xfce - Empty Apps Menu"
date: 2011-04-28
forum: Desktop Environments
---

### Post by Tacuabe on 2011-04-28
Hello, 
I'm using Ubuntu 11.04 and Xfce 4.8. For no apparent reason my Applications Menu (which worked OK) now shows "No applications found". After some googling I was able to find where the menu is: /etc/xdg/menus/xfce-applications.menu. I suppose it should be copied to another location to activate it. The big question is: WHERE? Help is welcome. I really like Xfce very much and miss this functionality now.

---

### Post by Copper Bezel on 2011-04-28
~/.config/menus/xfce-applications.menu, according to [the wiki]("http://wiki.xfce.org/howto/customize-menu"). = )

---

### Post by Tacuabe on 2011-04-28
Thanks! It worked flawlessly.

However, another problems are still unsolved. The right-click on the screen does not display the xfce menu. Presently there appears one that starts with "Create Folder", etc. I suspect that xfce is not using xfwm and that gtk is messing my desktop. (I just installed xfce with synaptic and Ubuntu and Ubuntu Classic are still available options at login time).

Besides, my destopk became full of my home folders (which I do not want there). But the Desktop folder is empty! How come?

Thanks for your invaluable help.

---

### Post by Copper Bezel on 2011-04-29
No problem, but I don't think I can be much more help on this - I'm primarily a Gnome guy and I'm still on Maverick, so my XFCE is still 4.6, and there were some big changes in between. Hopefully someone else can answer your questions, here. 

I can say this much, that xfwm isn't needed for the right-click menu on the desktop, which is a feature of xfdesktop itself (so that it, for instance, works under Compiz as well.) GTK is the shared default under XFCE and Gnome; there shouldn't be any compatibility problem there.

In Gnome, there's a gconf-editor option to alter Nautilus's behavior and choose whether the desktop displays the Desktop folder or the Home folder instead. I think, though, that the default folder locations in ~/.config/user-dirs.dirs are shared between the two DEs.That said, if your Gnome environment isn't having the same problem, that can't really be the issue, and the problem is probably with xfdesktop's own configuration. If you can purge it and reinstall it without causing any other problems, which will probably mean removing and reinstalling a number of other XFCE components (without removing *their* configuration data), you might be able to solve both problems.

---

### Post by Tacuabe on 2011-04-29
Thanks Copper Bezel. 

Your suggestions yielded the correct answer and everything is now back to normal. 

I did have the same problem with Gnome, so I edited the user-dirs.dirs and changed the entry that read "XDG_DESKTOP_DIR="$HOME/" to "XDG_DESKTOP_DIR="$HOME/Desktop". 

Since my Desktop file is empty I got a clean desktop in both DEs.

Additionally, the right-click menu now behaves correctly both for Ganome and Xfce.

---

### Post by Copper Bezel on 2011-04-29
Excellent!

Please mark the thread as solved. = )

---

### Post by John Bennett on 2011-06-22
> **Copper Bezel said:**
> ~/.config/menus/xfce-applications.menu, according to [the wiki]("http://wiki.xfce.org/howto/customize-menu"). = )

I had the same problem as Tacuabe.

I typed into the command line...
```
sudo cp /etc/xdg/menus/xfce-applications.menu ~/.config/menus/xfce-applications.menu
```...and the problem was instantly fixed.  Hot digity!  

Thanks Copper Bezel!!

---

### Post by fooey on 2011-07-26
worked for me too. thx

---

