---
title: "Need to remove item from open dialog, easy?"
date: 2006-01-26
forum: Desktop Environments
---

### Post by stalefries on 2006-01-26
One day, I was adding certain folders that I access frequently to the bookmarked folders part of the standard GNOME open dialog box. I accidentally added a folder to the universal bookmarks (like Computer and Filesystem) that is in my home folder and cannot be accessed by others. I can't remove it from that window, so I was wondering if there was some text file somewhere that I could edit, or some other simple thing to do, that would allow me to remove that entry. I have a screenshot, to show the problem.

---

### Post by Zalbor on 2006-01-26
I think "Documents" is added there by default... But to add or remove things there, what I do is open a program like gedit, click "open" or "save" then go to the directory and click "add".

There has to be an easier way to do it, but I've found none...

---

### Post by varunus on 2006-01-26
If you make a folder called "Documents", linux will treat it like your "My Documents" folder on Windows.  You can't get rid of it from there unless you call your Documents folder something else.

Other people shouldn't be seeing Documents there unless their home folders also have "Documents" links.

---

### Post by stalefries on 2006-01-26
I just tried renaming it, and it dissapeared. After re-renaming it back to Documents, it reappeared. does anyone know if and where there is some sort of configuration file that I can edit to remove this? Here's a slightly mor explanatory screenshot.

---

### Post by stalefries on 2006-01-28
/bump

---

### Post by varunus on 2006-01-29
You don't need the lower entry; if you want to use the documents folder, you should remove the lower entry.  Ubuntu allows users to have a "Documents" folder just like "My Documents" in windows, but it does not force you to unless you want to.  Really, just remove your bottom link (i'm pretty sure a right click and remove will fix that up) and the top one will stay...

Or, call it something like "username's documents" or something else.

Unfortunately, there's no way to turn the automatic "Documents Folder" off, so you'll have to rename it or accept that it'll be there up top (something done automatically by ubuntu).

---

### Post by stalefries on 2006-01-29
It wasn't done automatically. I accidentally added that one up there, and unfotunately, it shows for all users.

---

### Post by stalefries on 2006-01-30
[quote=varunus]
Unfortunately, there's no way to turn the automatic "Documents Folder" off, so you'll have to rename it or accept that it'll be there up top (something done automatically by ubuntu).[/quote]

Wait, it's automatic? I always thought I had done it...

---

