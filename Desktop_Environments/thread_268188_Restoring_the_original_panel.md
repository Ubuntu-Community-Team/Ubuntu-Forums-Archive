---
title: "Restoring the original panel"
date: 2006-09-29
forum: Desktop Environments
---

### Post by pikzel on 2006-09-29
Hi

I'm new to this forum (and to linux as well).
I accidentally removed some of the "gadgets" from my panel, and I can't seem to find them anywhere. I've tried addinig them back to the panel, but couldn't find the battery manager (the default, liked that one better) nor the nm-applet/wireless network manager. I've also tried searching the forums, but only found how to add a panel and contents to it, not restoring it all. 

Is there any way to restore the panels to their default mode? I suppose I could download a default config from somewhere.

Running gnome on dapper.
Thanks in advance :)

---

### Post by nthdegree on 2006-09-29
Disclaimer: THIS IS CRAZY! PLUS I'M A KDE USER MAINLY!!!

What you want to do is this to restore a default config.

Open up a terminal, then put:

```
mv ~/.gnome ~/.gnome-backup
mv ~/.gnome2 ~/.gnome2-backup
```

That should, fingers crossed mean that next time you login it will load with a default config :)

If there's a problem do the following to restore:
```
mv ~/.gnome-backup ~/.gnome 
mv ~/.gnome2-backup ~/.gnome2 
```

---

### Post by komputes on 2007-12-13
I would like to share this, since I had the same frustrating issue with panels. They are way too easy to remove and change since they can't be locked. This command + rebooting will bring back the default panels. 

You will first need to get a terminal up. Since you don't have a menu bar/panel, that is quite tricky, but there is a keyboard shortcut for this:

Alt+F2 (This is equivalent to a run command)

from here you have a choice of which terminal you want to use, the default is **gnome-terminal** (which is a bash terminal) or you can also use **xterm** as well.

Once you have a terminal window open it is pretty simple to restore the default panels (as they were when you first installed Ubuntu). In the terminal type:

```
sudo debconf gnome-panel
```

Close the terminal, reboot, et voila!

:popcorn:

---

### Post by TomeRaider2 on 2007-12-30
How lon does it usually take to run the command? Mine was still running after about 10 minutes. When I closed the terminal window, the panel reverted back to the one I had messed up.
 
> **komputes said:**
> I would like to share this, since I had the same frustrating issue with panels. They are way too easy to remove and change since they can't be locked. This command + rebooting will bring back the default panels. 
[snip]

Once you have a terminal window open it is pretty simple to restore the default panels (as they were when you first installed Ubuntu). In the terminal type:

```
sudo debconf gnome-panel
```

Close the terminal, reboot, et voila!

:popcorn:

---

### Post by urukrama on 2007-12-30
You can just delete the gnome-panel configuration files in your home directory. You will find them in /home/USERNAME/.gconf/apps

Delete or remove the entire directory called "panel". Kill the panel with "killall gnome-panel"; it should automatically restart. If not, start it with the command "gnome-panel"

I've just tried this on my computer and it works fine. (And I also run Dapper)

---

