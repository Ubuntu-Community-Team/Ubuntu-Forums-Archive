---
title: "Add terminal launcher to panel in Xubuntu, xfce"
date: 2006-11-29
forum: Desktop Environments
---

### Post by vodsonic on 2006-11-29
I tried to add a launcher that will open a terminal to the panel in Xfce in Xubuntu 6.10 (Edgy Eft). I found useful information about adding launchers to the panel in the following two threads.

launcher in Xubuntu
[http://www.ubuntuforums.org/showthread.php?t=255716](http://www.ubuntuforums.org/showthread.php?t=255716)

Easy Xubuntu launcher
[http://www.ubuntuforums.org/showthread.php?t=277114](http://www.ubuntuforums.org/showthread.php?t=277114)

However, to use either of these, you must know the exact file path of the executable that you want the launcher to start. 

I couldn't figure out where "Terminal" resides, or if that's even what the executable is called. Xfce doesn't differentiate between a left or right mouse click when I'm in the Applications menu. In other window managers & OS'es, I would typically try a right click on the item in the menu to get its properties.

I poked around in the file system, and eventually happned upon a symlink to Terminal, in /usr/bin. Right click, properties, revealed the name of the executable (xfce4-terminal), but not its location.

Opening a terminal, I used whereis at the command line:

[B]user@linux:~$ whereis xfce4-terminal
xfce4-terminal: /usr/bin/xfce4-terminal /usr/bin/xfce4-terminal.wrapper /usr/lib/xfce4-terminal /usr/X11R6/bin/xfce4-terminal /usr/X11R6/bin/xfce4-terminal.wrapper /usr/bin/X11/xfce4-terminal /usr/bin/X11/xfce4-terminal.wrapper /usr/share/man/man1/xfce4-terminal.1.gz
[/B]
I'm not sure which of these instances is the main one, or if all but one are actually symlinks, but I tried the first one.
[B]
So, here you go:[/B]

To set up the launcher, right click on the panel and select Add New Item. The default option selected in the next screen is Launcher, which is what you want. Click Add.

On the next screen, enter the name and description of your choice (I just used "Terminal" in both fields.) The icon selector just happens to have a handy terminal icon - select that.

In the "Command" field, enter /usr/bin/xfce4-terminal

Click "Close" and you're done.

Hopefully other noobs like myself will find this helpful.;)

---

### Post by kerry_s on 2006-11-30
Or you can launch xfce4-appfinder & just drag the application to the properties window of the launcher(the big box that has the app name).

You don't need the full path to the name, just put the name of the app(ie: xfce4-terminal) for the command, but if you need the full path it's /usr/bin/(app) those are the user apps.

---

### Post by floundered on 2007-01-23
Thanks kerry_s!  Makes me think there should be a button in the XFCE panel launcher properties window to open the app finder, or something like it.

---

