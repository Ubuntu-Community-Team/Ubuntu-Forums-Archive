---
title: "Nautilus &quot;misbehaving&quot; since upgrade"
date: 2005-11-30
forum: Desktop Environments
---

### Post by thewayofzen on 2005-11-30
Ive been using ubuntu breezy since a month before the official release.  Gnome and nautilus in particular have been working great the entire time until the upgrade i did last week.  

Now as a result of upgrading nautilus i am experiencing problem with my desktop icons.  When i insert blank cdr's into my writer and burn a cd it is happening quite frequently that the "Blank CD-R Disc" icon remains on the desktop.   If i insert another cdrom disc into the drive it will automount as usual and then i will have TWO cdrom discs on the desktop. (i only have one cdr drive)

Ive tried getting ride of it with the eject command and it opens the tray to let me to remove a disc that isnt even present.  Ive never had this problem before and seem to be in a position where the only solution is hitting  CTRL ALT BKSPC to restart GDM or rebooting outright.  Its a pain. 

Is anyone else experiencing this.. and is there a fix that anyone is aware of?

Thanks.

zen

---

### Post by dcstar on 2005-11-30
[QUOTE=thewayofzen]Ive been using ubuntu breezy since a month before the official release.  Gnome and nautilus in particular have been working great the entire time until the upgrade i did last week.  
......
Is anyone else experiencing this.. and is there a fix that anyone is aware of?

Thanks.

zen[/QUOTE]
I gave up on using the Nautilus CD burner in Breezy (I've even uninstalled it, since it refused to work post upgrade), and as well I've even installed the pmount package to replace the (now) unreliable Nautilus one.

So yes, other people are having problems......         :(

---

### Post by thewayofzen on 2005-11-30
pmount?  will a simple  'sudoapt-get install pmount' have this automatically take its place as the default.. and will it work in the same manner?  or do i need to edit a config file?
I know im likely being a BABY but having an unremoveable icon show up is a pain in the but.. and having had it not work that way before.. id like to think it can be fixed someway other then restarting my machine.

zen.

---

### Post by dcstar on 2005-12-09
[QUOTE=thewayofzen]pmount?  will a simple  'sudoapt-get install pmount' have this automatically take its place as the default.. and will it work in the same manner?  or do i need to edit a config file?
I know im likely being a BABY but having an unremoveable icon show up is a pain in the but.. and having had it not work that way before.. id like to think it can be fixed someway other then restarting my machine.

zen.[/QUOTE]
Pmount seems to work straight after install, the only real difference I noticed (apart from Automount actually working now......) is that the System-Preferences-Removable drives menu item is replaced with System-Preferences-CD and DVD.

That is the only configuration you have to do - put in the programs you want to run for each type of disk.

---

