---
title: "Confirm before moving to trash"
date: 2007-04-22
forum: Desktop Environments
---

### Post by MR Bacardi on 2007-04-22
I have just gotten my parents to switch to Ubuntu :)
However, they are missing the "Are you sure you want to delete this file?" before even moving the file to the trash.
I can't seem to find it anywhere. Isn't it possible?

---

### Post by Swab on 2007-04-22
I'm not aware of any way to do that, however you should be prompted before emptying the trash.

---

### Post by jubjubrsx on 2007-04-22
i swore i saw that in gconf somewhere before prompt before delete or something...

just open a terminal gconf and look through that...

---

### Post by brianC on 2007-04-22
Open your home folder
go to edit
preferences
behavior
at the bottom check for " ask before emptying the trash  or deleteing files"

---

### Post by MR Bacardi on 2007-04-22
> **jubjubrsx said:**
> i swore i saw that in gconf somewhere before prompt before delete or something...

just open a terminal gconf and look through that...

I found the following:
/apps/nautilus/preferences/confirm_trash
But eventhough it is set to true, I do not get any confirmation dialog?

---

### Post by MR Bacardi on 2007-04-22
> **brianC said:**
> Open your home folder
go to edit
preferences
behavior
at the bottom check for " ask before emptying the trash  or deleteing files"
Checked, but no prompt when pressing Delete, only if I empty the trash

---

### Post by brianC on 2007-04-22
Doing a search a few other people have had the same problem, with no luck solving . Sorry I couldn't be of more help.

---

### Post by MR Bacardi on 2007-04-23
Isn't it some kind of a bug then? And should be filled as one?

---

### Post by naked on 2007-04-25
I would also like to be able to turn this feature on.  Seems like it existed in versions past.  Not that most people would want this.  If there was a way to restore an item to its original location from within the trash folder, then I might not need this option.

Any thoughts?

L

---

