---
title: "Kubuntu Hardy - no icon for gedit"
date: 2008-06-10
forum: Desktop Environments
---

### Post by retrovertigo on 2008-06-10
I installed the Hardy "KDE4 Remix", and also installed KDE3 alongside it.  I am using KDE3 as my primary desktop environment, though.  I then installed gedit via apt since I prefer it to kate.  However, no icons were apparently installed for it.  There is no icon on the K Menu for gedit (which is called Text Editor in this menu), and there are no files for gedit within /usr/share/pixmaps or /usr/share/icons.  I do not have a ~/.icons directory.  I tried making a desktop item out of its entry from the K Menu, and then opened the .desktop file in vi and it appears to be trying to use an image called "accessories-text-editor".  There is no such file in /usr/share/.

Anyone else experiencing this issue?

---

### Post by editrix on 2008-06-14
Do you have gnome installed as well? Because I don't think their icons come with KDE.

I have both installed and ```
/usr/share/icons/crystalsvg/16x16/apps/dlgedit.png
/usr/share/icons/crystalsvg/32x32/apps/dlgedit.png
```

You could, of course, use any icon you like--including one you've created

---

