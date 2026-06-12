---
title: "icon duplication when draging on desktop problem."
date: 2007-07-01
forum: Desktop Environments
---

### Post by CodyS on 2007-07-01
I have been using Ubuntu for about 6 months,  suddenly a strange problem has appeared about a week ago.

When I left click and drag an icon on the desktop it shows the little + and copies the icon when I drop it. If i hold down the shift key, it moves the icon as one would expect.

I have not had this problem before, and I have not been able to find anywhere to change this. It's acting as though my keyboard has the shift key reversed. I have tried different keyboards even.

I have spent hours gong through the various gconf-editor settings to no avail.

Other than this weird behavior, everything works fine.

Any help here would be much appreciated.

---

### Post by jpeddicord on 2007-07-03
Go to System > Preferences > Keyboard, Layout Options tab. See if there is anything odd there (changes are in **bold**). You should be able to change the Shift action if it is acting weird.

If nothing is awry there, it might be a permissions setting. Check the permissions of the folder you are dragging from: if the folder has Write access, it should default to Move. If you don't have write access to the folder you are copying from, it will default to Copy (the +).

If neither of those helps, then I am out of solutions. Try doing a software update and seeing if it helps.

Jacob

---

### Post by CodyS on 2007-07-04
I found it!.. your suggestion about permissions was the key.
It turns out the Desktop folder had the wrong permissions set. Once I reset the correct permissions to it, all is well again.

Thank you

---

