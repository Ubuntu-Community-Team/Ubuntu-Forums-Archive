---
title: "Kubuntu: OpenOffice Quickstarter"
date: 2006-07-08
forum: Desktop Environments
---

### Post by jongkind on 2006-07-08
The OpenOffice Quickstarter works fine when I log into Gnome. This is not the case with Kubuntu. How can I solve this issue?

In addition to that: how can I make that programs start automatically when I log in to Kubuntu (e.g. gmail-notifier; I'm aware how this can be accomplished in Gnome).

---

### Post by ajgreeny on 2006-07-08
Just add the links to the folder ~/.kde/Autostart and they will start with KDE.  I have the OOo quickstart which I added with a new link to:-

ooffice -quickstart -nologo -nodefault

and all works wonderfully.  OOo starts from cold, as it were, in about 4 - 5 secs, which is pretty good.  It took much longer with version 1.0.3 or whatever it was in Breezy.

---

### Post by jongkind on 2006-07-08
I added the line below to the end of the autostart file. It did not help though.

/usr/bin/ooffice -quickstart -nologo -nodefault

---

### Post by ajgreeny on 2006-07-17
Are you certain OOo doesn't start quicker with this running at start-up?  If you want the icon in the system tray, however, install *oooqs-kde* and I think that will do it for you.

Be warned, however.  Just to try it out, I have just installed oooqs-kde on my kubuntu machine and find that with that running my cpu load shown in the Gnome system monitor (I have both desktops installed) is near 100% all the time.  Quitting it from the icon brings cpu load back down to between 1% and 3%, as I normally get.  Using "top" in the terminal gives me low cpu load so I wonder if this is just a bug.  However, the mouse cursor movement when oooqs is runing is very jumpy, so I'm sure something is not quite right.

Any thoughts anyone.

---

### Post by jongkind on 2006-07-17
Yes, I solved this, thanks for your help.

---

### Post by ajgreeny on 2006-07-17
Did you have the same problem with cpu load or was your install of oooqs-kde OK?  I've uninstalled it and gone back to the *ooffice -quickstart -nologo -nodefault* link again instead where everything is working properly.

---

