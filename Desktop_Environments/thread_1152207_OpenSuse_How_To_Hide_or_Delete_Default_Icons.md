---
title: "OpenSuse How To Hide or Delete Default Icons?"
date: 2009-05-07
forum: Desktop Environments
---

### Post by djoe on 2009-05-07
I installed OpenSuse on a second computer, but how do I hide or delete these icons on the desktop?:

User's Home
OpenSuse [locked]
OnlineHelp [locked]

---

### Post by wsonar on 2009-05-07
gconf-editor

apps/nautilus/desktop

---

### Post by djoe on 2009-05-07
By apps you mean Application Menu?:confused:

---

### Post by wsonar on 2009-05-07
Sorry for not being clear

you will need to open a terminal which is under accessories

then type gconf-editor

then navigate apps/nautilus/desktop

see screenshots

---

### Post by djoe on 2009-05-07
I found it under Applications and System.  But that's ok, I was able to Hide the Home Folder.

Now I just need some way to UnLock and Hide or Delete the OnlineHelp and OpenSuse Icons that are on the DeskTop.

It says that moving the icon anywhere on the desktop is locked.

---

### Post by wsonar on 2009-05-07
you will need to have super user privileges you can delete from a terminal window

sudo rm ~/Desktop/filename

here's a similar thread

[http://forums.opensuse.org/pre-release-beta/401122-remove-icons-gnome-desktop.html]("http://forums.opensuse.org/pre-release-beta/401122-remove-icons-gnome-desktop.html")

---

### Post by djoe on 2009-05-07
If I installed OpenSuse, does that mean I'm a super user by default?

Isn't Admin a SuperUser?:-s

---

### Post by wsonar on 2009-05-08
By reading the opensuse forum it appears they are located here

/usr/share/dist/desktop-files

you would not have permission to remove stuff from here unless you do sudo

you can also right click on the file on the desktop to verify where they are located

I would open a terminal

cd /usr/share/dist/desktop-files

from there I would do ls which should show the name of the files 

then I  would do sudo rm filename
--------------------------------------------------------------------
the rm command will completely remove the file from your HD, use it with caution possibly read the man page on it and only remove the file if your sure that's what you want to do, in this case being a link on they desktop they don't want you to remove for some odd resson it is ok.
--------------------------------------------------------------------

see this thread for the exact issue
[http://forums.opensuse.org/applications/412377-how-remove-opensuse-online-help-icon-desktop.html]("http://forums.opensuse.org/applications/412377-how-remove-opensuse-online-help-icon-desktop.html")

---

### Post by djoe on 2009-05-09
Ok, I'll give that a try.

---

### Post by djoe on 2009-05-13
ERROR:
rm: cannot remove `OnlineHelp': No such file or directory
rm: cannot remove `OpenSUSE': No such file or directory

I notice the root password doesn't type in, is that normal?

---

