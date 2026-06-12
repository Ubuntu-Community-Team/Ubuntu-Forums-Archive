---
title: "Gnome desktop area &quot;broken&quot;"
date: 2007-03-13
forum: Desktop Environments
---

### Post by rljacobson on 2007-03-13
I sat down at my computer one day and noticed my desktop background picture was missing (in Gnome). Moreover, I couldn't right-click on the desktop to bring up the usual context menu, I couldn't click-and-drag the usual selection field, and any files I put in the /home/username/Desktop directory were not displayed.

I clicked System->Preferences->Desktop Background and my background picture magically reappeared without changing any settings. But my desktop is still broken in the sense that right-clicking does not bring up the usual context menu and no files are displayed on the desktop.

What should I do?

---

### Post by rljacobson on 2007-03-13
I have solved my own problem. On a hunch I renamed the file
/home/username/.gnome2/session
to
/home/username/.gnome2/session.old .

This solved my problems.

---

### Post by Dr. Nick on 2007-03-13
Ive never had that happen, but similar goofy issues can be solved by renaming some of the gnome folders like .gnome etc, It basically just resets most of the gnome options.

---

