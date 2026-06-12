---
title: "Threw out the wastebasket"
date: 2005-07-31
forum: Desktop Environments
---

### Post by drwhom on 2005-07-31
I accidently removed the wastebasket.  When I put the applet back and try to delete, I receive the error that I do not have permission.  Any thoughts?

drwhom

---

### Post by Magneto on 2005-07-31
did you delete something using sudo?

---

### Post by kassetra on 2005-08-01
[QUOTE=drwhom]I accidently removed the wastebasket. When I put the applet back and try to delete, I receive the error that I do not have permission. Any thoughts?

drwhom[/QUOTE]

You might want to check the permissions on /home/your_user_name/.Trash 
if you don't have read/write privileges to that directory then you won't be able to trash anything.

If you don't know how to check the permissions or to set them do this: (I'm assuming you're using gnome)
-Show hidden files & folders first in Nautilus-
1. Places->Home Folder
2. Edit->Preferences
3. Checkmark the "Show hidden and backup files" box.
4. Close the Preferences dialog box.

-Check .Trash-
1. In Nautilus, scroll down until you see the .Trash folder.
2. Right click on the folder.
3. Left click on Properties.
4. Click on the Permissions tab.
5. Now, I have: Owner - Read Write & Execute, Group - Read Write & Execute, and Others - Read & Execute.  You probably want to have something similary checkmarked.

-If you need/want to change your permissions-
1. Simply checkmark the boxes you want (Permissions tab above), and then click close.

---

### Post by Sam on 2005-08-01
[QUOTE=drwhom]I accidently removed the wastebasket.  When I put the applet back and try to delete, I receive the error that I do not have permission.  Any thoughts?

drwhom[/QUOTE]
Type this in a terminal:
```
$ sudo rm -rf ~/.Trash/*
```

---

### Post by drwhom on 2005-08-01
Thanks for the great ideas.  It turns out I had a copy of my grub folder in there that it did not want to delete.

drwhom

---

