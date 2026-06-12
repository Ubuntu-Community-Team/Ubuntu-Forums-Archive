---
title: "[SOLVED] Fonts"
date: 2008-08-21
forum: Desktop Environments
---

### Post by claymater on 2008-08-21
OK so I have a few fonts I wanna add, but when I go to the fonts folder (/usr/share/fonts) It wont let me put my folders in.. it keeps giving me a "There was an error moving the file into /usr/share/fonts." And wanting me to skip it.. What do I do?

---

### Post by Cheesehead on 2008-08-21
As a *user* you don't have permission to tinker with the /usr/share/fonts folder.

You can do it as an *admin*, but there's an even better way - the right way.

THE RIGHT WAY FOR A USER (*easiest*):
1) Create a new folder called '.fonts' in your home directory. *No sudo or special commands needed*
2) Put the fonts in.
3) Restart the app you want to use, and fonts from BOTH folders (/usr/share/fonts and /home/USER/.fonts) should be automatically loaded.
One big advantage of this method is that your normal /home backups will backup the fonts, too. You won't lose the fonts if you ever lose your system.

THE RIGHT WAY FOR AN ADMIN:
This method really only makes sense for a multi-user system. The admin (you) puts the fonts in the /usr/share/fonts folder.
1) Open a file manager with admin permissions. If you use Nautilus, the command is 'gksudo nautilus'
2) Move the fonts.
3) Close the window when finished - it has admin permissions.

---

### Post by claymater on 2008-08-21
Oh thanks! Worked great!

---

### Post by rotwang888 on 2008-08-22
Yes- works like a dream.  I just hope that the powers that be know that the help center says to go to system>preferences>fonts, which doesn't exist.

---

