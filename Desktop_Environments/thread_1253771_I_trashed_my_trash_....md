---
title: "I trashed my trash ..."
date: 2009-08-30
forum: Desktop Environments
---

### Post by xander.miller.ferrari on 2009-08-30
I use a couple of different users.
On one user I was deleting files and I deleted the trash folder itself.
Immediately I undid the deletion ( I think by hitting the right mouse button ) and choosing "undo Trash".
The trash icon was restored.

From then on I have no functional trash bin anywhere. If I log in as a different user I cannot send items to the trash (it says it is full), I cannot empty the trash, and there are no apparent files in the trash bin. It does not matter what user I log in as.

Is there a package which the trash bin is part of? I'd like to do something like:
sudo apt-get purge whatevertrashpackage

and then

sudo apt-get install whatevertrashpackage

Incidentally, it seems to me a security issue for one user to be able to destroy functionality for other users without using sudo.

I am using Kubuntu 9.04 and I've installed gnome as well, I'm running KDE.

---

### Post by aysiu on 2009-08-30
I don't know if KDE does trash the same way Gnome does, but you can try pasting these commands into the terminal: ```
sudo chown -R *username:username* /home/*username*
cd ~/
mkdir -p .local/share/Trash/files
mkdir -p .local/share/Trash/info
mkdir -p .local/share/Trash/expunged
``` where *username* is your actual username.

Then see if you add the trash applet back to the Gnome panel if you can empty and/or use the trash.

---

### Post by aysiu on 2009-08-30
I don't know if KDE does trash the same way Gnome does, but you can try pasting these commands into the terminal: ```
sudo chown -R *username:username* /home/*username*
cd ~/
mkdir -p .local/share/Trash/files
mkdir -p .local/share/Trash/info
mkdir -p .local/share/Trash/expunged
``` where *username* is your actual username.

Then see if you add the trash applet back to the Gnome panel if you can empty and/or use the trash.

---

