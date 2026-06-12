---
title: "How to reset the all users' settings in Gnome?"
date: 2007-04-22
forum: Desktop Environments
---

### Post by grenier on 2007-04-22
I've just installed feisty, and I'm facing a problem. I'm a long time linux user (mainly Mandriva) and as such, there are lots of things on my account that I can't lose, and some that are a problem: though I haven't used gnome in Mandriva or other distros in a long time, there are remnants of previous settings.

I've tried erasing various .gnome, .gnome2, .gconf and .gconfd directories, but it wasn't enough.

So, what must I do to be able to start on that account with fresh, default ubuntu settings?

---

### Post by jpeddicord on 2007-04-23
You have to erase the settings in terminal mode, otherwise GNOME will rewrite them at the end of your session. To do this, logout and go the session menu. Choose "Failsafe Terminal" for the session type, and login again. Then, in the terminal that appears, type this command:
```
rm -r .gnome .gnome2 .gconf .gconfd
```Feel free to add any other folders to the end of that if they keep their settings.
Logout by typing "exit," change your session back to Default, and be welcomed back to a vanilla Ubuntu.

---

### Post by ComplexNumber on 2007-04-23
after logging into failsafe terminal, it may be better to use these commands instead of removing them permanently:

mv .gconf .gconfOLD
mv gconf .gcondOLD
mv .gnome .gnomeOLD
mv .gnome2 .gnome2OLD
mv .metacity .metacityOLD
mv .nautilus .nautilusOLD
mv .gtk-bookmarks .gtk-bookmarksOLD
mv .local .localOLD
mv .bash_profile .bash_profileOLD
mv .bashrc .bashrcOLD


that pretty much covers all or most of te system files and directories. then as the above poster says, exit back out and log in with gnome. the directories and files will be reacreated as if you'd only just installed it.

---

### Post by grenier on 2007-04-26
Well, that did the trick.
Looking over each of the directories, I guess the one I'd forgotten was .nautilus.

Thanks

---

