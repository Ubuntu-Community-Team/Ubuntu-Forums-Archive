---
title: "Make Nautilus as File Manager"
date: 2010-12-13
forum: Desktop Environments
---

### Post by sid.mallya on 2010-12-13
Hey,

I have, in fact, stated my problem correctly. I want to make Nautilus as the default File Manager in KDE. I use GNOME on other computers, and don't like the feel of the KDE file manager on my PC. I looked online but most "solutions" are for the other way round and in either case, didn't work for me.

I tried changing the 'inode/directory' file association to Nautilus but it didn't change anything. What can I do ?

(I have GNOME as a DE here too .. But I would like to know how to change the association in KDE as well)

- Sid :D

---

### Post by ajgreeny on 2010-12-13
I have no idea if this will work or not, but here is a script file put together by psychocats, I think, in order to put things back to normal for users who had moved away from using nautilus as their default file manager in gnome.  This script put back nautilus as the default, so may help you, either as it is, or may give you some idea on how you can edit this to get nautilus as default.  I suspect, however that some of the .desktop files this script points to will not exist on you system, as you don't presumably have the gnome desktop on the computer.  You could, of course add gnome alongside kde and then this script might work but that's all getting a bit messy.
```
#!/bin/bash
if [ -f /usr/share/applications/nautilus-computer.desktop.backup ]; then
  echo -e "\nRestoring Computer .desktop file\n"
  sudo cp /usr/share/applications/nautilus-computer.desktop.backup /usr/share/applications/nautilus-computer.desktop
else
  echo -e "\nYou're missing a Computer .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/nautilus.desktop.backup ]; then
  echo -e "\nRestoring Nautilus .desktop file\n"
  sudo cp /usr/share/applications/nautilus.desktop.backup /usr/share/applications/nautilus.desktop
else
  echo -e "\nYou're missing a Nautilus .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/nautilus-folder-handler.desktop.backup ]; then
  echo -e "\nRestoring folder handler .desktop file\n"
  sudo cp /usr/share/applications/nautilus-folder-handler.desktop.backup /usr/share/applications/nautilus-folder-handler.desktop
else
  echo -e "\nYou're missing a folder handler .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/nautilus-home.desktop.backup ]; then
  echo -e "\nRestoring Home .desktop file\n"
  sudo cp /usr/share/applications/nautilus-home.desktop.backup /usr/share/applications/nautilus-home.desktop
else
  echo -e "\nYou're missing a Home .desktop backup file--nothing to restore\n"
fi
if [ -f /usr/share/applications/network-scheme.desktop.backup ]; then
  echo -e "\nRestoring Network .desktop file\n"
  sudo cp /usr/share/applications/network-scheme.desktop.backup /usr/share/applications/network-scheme.desktop
else
  echo -e "\nYou're missing a Network backup file--nothing to restore. If you had Thunar as your previous default file manager, this is normal.\n"
fi
echo '
Nautilus should now be your new default file manager in Gnome again
```

---

### Post by sid.mallya on 2010-12-14
Okay .. I am a lil' apprehensive to try out scripts .. Either way, Ill read it and see if it is possible. Thank you.

Btw, this changes the file manager in GNOME to Nautilus. I am guessing, KDE script would be different (since it uses all that k-crap) ?

---

### Post by ajgreeny on 2010-12-14
> **sid.mallya said:**
> Okay .. I am a lil' apprehensive to try out scripts .. Either way, Ill read it and see if it is possible. Thank you.

Btw, this changes the file manager in GNOME to Nautilus. I am guessing, KDE script would be different (since it uses all that k-crap) ?
Yes, probably, which is why I said I don't know if this will work, nor if you will have some of the files this script points to.

---

### Post by I_can_see_the_light on 2010-12-14
Is it not working by going to System Settings > Default Applications > File Manager?

---

