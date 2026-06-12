---
title: "finding files the ultimate irony"
date: 2007-03-14
forum: Desktop Environments
---

### Post by 900donuts on 2007-03-14
(i apologize for any misspelling)
heres the situation

every time ive tryed to find anything with ubuntu default search utility it didn't work

so i decided to get beagle

i went to synaptic and installed the package

and you can all guess what happend next......


for those who havn't guessed. I CAN'T FIND BEAGLE!!!

a little help please?

---

### Post by yabbadabbadont on 2007-03-14
Open Synaptic.  Select the Beagle package.  Click on properties.  Click on the "Installed Files" tab.

---

### Post by 900donuts on 2007-03-14
ok i see it but what do i punch in to launch beagle?
and how do i make it easy to access?

---

### Post by yabbadabbadont on 2007-03-14
If there isn't a menu option for it, try logging out and back in again.  If it still doesn't appear in the menu, then it could be that it is only available as a gnome-panel applet.  In which case you would right-click on the panel, choose "Add to panel", and search for beagle there.

---

### Post by 900donuts on 2007-03-14
no luck i re logged back in still no beagle

---

### Post by yabbadabbadont on 2007-03-14
Assuming that you are using gnome, hit alt-f2, type beagle into the box, hit enter.  If it comes up, then open a terminal window and type "which beagle" without the quotation marks.  It should give you the path to use for creating a custom launcher.  I've no idea why a menu entry wasn't created for you.  File a bug at [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

EDIT: It appears that it is a known bug... (aren't you lucky ;))  [https://launchpad.net/ubuntu/+source/beagle/+bug/52878](https://launchpad.net/ubuntu/+source/beagle/+bug/52878)

---

### Post by kerry_s on 2007-03-14
Check
Right click the panel add app.
or
press alt+F2 type beagle
create a launcher.

---

