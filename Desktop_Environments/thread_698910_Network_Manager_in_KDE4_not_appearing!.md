---
title: "Network Manager in KDE4 not appearing!"
date: 2008-02-16
forum: Desktop Environments
---

### Post by soumen08 on 2008-02-16
I installed KDE4 through the terminal a few days ago and i cant  see the network icon in the notification region.
I have a HP6515b Laptop running ubuntu 7.10. i use ndiswrapper to configure the winxp driver for the broadcomm wireless into ubuntu. In gnome it works just fine.Besides the volume control also isn't there in KDE4's notification area while it appears in gnome!
Are there services which need to be started before i can see the above 2?Please help me!
Thanks in advance!

---

### Post by Bubba64 on 2008-02-16
Right click in the bar hit add to panel and find the icons hit add and you should have it you can also access it through system-administration network,You could also drag and drop the network from administration into the bar.

---

### Post by prann on 2008-02-17
If I right click the bar, I only get Remove this Task Manager and Task Manager Settings there is no Add. I would like to add the volume control.

---

### Post by Matakoo on 2008-02-17
> **prann said:**
> If I right click the bar, I only get Remove this Task Manager and Task Manager Settings there is no Add. I would like to add the volume control.

You add plasmoids by moving the pointer to the widget in the top-right corner. If you don't get a "Add widgets" in the pop-out menu, first right-click on the desktop and choose "Unlock widgets".

When you have the "Add widgets" window open, just find whatever you need and drag it to the taskbar.

As far as the volume control goes, you can get that into the taskbar by just hitting alt-f2, type kmix into the field and launch the program.  I don't think the network monitor has been ported to KDE4 yet though.

---

### Post by smyrman on 2008-04-06
> Are there services which need to be started before i can see the above 2?Please help me!
 Thanks in advance!

You need theese packages installed:
[I]kmix-kde4
network-manakger-kde[/I]

The last one is an kde3 app, but for now, that have to do.
First, Alt + F2 and write
```
knetworkmanager
```

To make sure that kmix starts at every login, create the file
~/.kde4/Autostart/kmix
Make it look like this:
```
#!/bin/bash
kmix; dcop kmix kmix-mainwindow#1 hide 
```

when your, done do this in a console:
```
chmod u+x ~/.kde4/Autostart/kmix
```


Edit: now your system should start knetworkmanager and kmix at every login (even if you set the "Restore manual saved session" option in 'System settings > Advanced > Session Manager')

---

