---
title: "about deleted files and trash bin..."
date: 2009-05-05
forum: General Help
---

### Post by mendozaro on 2009-05-05
I was wondering if there is a way to setup the trash bin so that all the deleted files WILL NOT GO IN THERE.

Background: at the beginning of windows era (win 95) i had computers with rather small hard drives... so i got used to NOT USE trash bin and the undelete option. Instead i double check what i delete... I am like that ever since. Now, being a ubuntu user, i didnt find any way so that the files will not go in the trash and i end up with lots of "deleted" but actually not deleted files.

Best regards.

---

### Post by mcduck on 2009-05-05
I don't think so. But if you want you can enable the option in the right-click menu to delete files directly (without using the trash bin). Just go to file manager's settings (edit/Preferences) and on the Behavior-tab you'll find the option "Include a Delete command that bypasses Trash".

Also, shift+del will bypass the trash bin.

---

### Post by Grenage on 2009-05-05
[http://ubuntuforums.org/showthread.php?t=48246](http://ubuntuforums.org/showthread.php?t=48246)

Bottom post.

---

### Post by AlexDudko on 2009-05-05
Open nautilus, choose Edit -> Properties -> Behavior and select "Include a Delete Command that bypasses Trash".

---

### Post by mendozaro on 2009-05-05
THANKS Grenage!

The answer is:

> You need to run Gnome Conf Edit, just pres alt-f2 and run: gconf-editor

Go to: apps/nautilus/preferences/enable_delete

This was a really fast answer / fix. I doubt it that any payed service will ever do like this!

Best regards.

---

