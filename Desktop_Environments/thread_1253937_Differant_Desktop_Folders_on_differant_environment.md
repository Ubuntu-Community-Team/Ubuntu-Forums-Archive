---
title: "Differant Desktop Folders on differant environments"
date: 2009-08-30
forum: Desktop Environments
---

### Post by Iksf on 2009-08-30
Is there any way to make GNOME look at lets say /home/user/GNOME, and KDE to look at /home/user/KDE. Because with KDE and being able to scroll as a folder i put much more in it than fits on a GNOME desktop, and if i make KDE look at a differant folder i get loads of .desktop extensions and other such problems

Any Ideas?

---

### Post by XubuRoxMySox on 2009-08-30
It's very difficult to figure out what you are asking... but regardless of what desktop environment you're using, in either one you have only one */home* folder.

All your applications appear in *usr/share/applications*. You documents appear in */home/documents* whether they were created in GnomeOffice or KWord or whatever else, unless you specify some other place.

You may _create_ separate folders _within_ your */home* directory if you wish, though I can't imagine why you would wish to.

-Robin

---

### Post by Iksf on 2009-08-31
I specificly mean which folder each desktop environment uses as its Desktop folder, instead of both using ~/Desktop

---

### Post by zhocchao on 2009-08-31
It is possible. But I don't know any easy way. I could look for what you need. But you should be able to write a Bash script, Repair your home if something goes wrong, and be prepared to encounter problems, as I heard that auto refresh of Desktop could be damaged (It's working fine on my comp).

---

### Post by Simian Man on 2009-08-31
I always rename my "Desktop" folder to "desktop" under Gnome because I hate capitalized folder names.  Gnome always respects that change, so perhaps you can try renaming "Desktop" to Gnome-Desktop under Gnome and then creating a new directory called Desktop.  Hopefully KDE will continue using that.

I don't use KDE, so I can't check...

---

### Post by Iksf on 2009-09-01
Simian i tried what you suggested and both Desktop environments updated unfortunalty, any other ideas

---

