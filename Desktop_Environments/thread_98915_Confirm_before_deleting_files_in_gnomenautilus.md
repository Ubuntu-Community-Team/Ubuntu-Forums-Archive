---
title: "Confirm before deleting files in gnome/nautilus?"
date: 2005-12-04
forum: Desktop Environments
---

### Post by naked on 2005-12-04
Several times I've deleted things that I haven't wanted to, usually just by accident or my son starts poking at buttons on the keyboard.  Is there a way to have a confirm box pop up whenever I try to delete something?

Usually it is in a folder with 20+ files, so trying to pick the one that was accidentally deleted and find it in the trash in sometimes difficult and always annoying.

Thanks!

L

---

### Post by manicka on 2005-12-04
In Nautilus go to Edit-->Preferences, then to the 'Behaviour' Tab

Makes sure that 'Ask before Emptying the Trash or Deleting files' is checked.

---

### Post by davmac on 2005-12-04
If you start up the configuration editor (Applications -> System Tools -> Configuration Editor).

Navigate to apps -> nautilus -> preferences and then make sure the "confirm_trash" has a tick mark next to it.

Hope this helps,

Dave Mac

---

### Post by naked on 2005-12-04
I have this done, but still it just deletes the files with no confirmation?

---

### Post by manicka on 2005-12-04
[QUOTE=naked]I have this done, but still it just deletes the files with no confirmation?[/QUOTE]

Are you choosing 'Delete' or 'Move to Trash'? Did you restart the session after making the changes?

You should get a confirmation message with 'Delete' but not with 'Move to Trash'. You should also get a confirmation when you empty the trash.

Edit: Reading your post again, it would seem that I have misunderstood what you were asking for. I don't think there is a way to get a confirmation message just for trashing a file, only emptying the trash. Having no confirmation message for trashing files is the default behaviour in gnome.Tthe confirmation only comes when you want to permanently delete them

---

### Post by naked on 2005-12-04
Hum.  Is there a way to disable the 'trashing' so that it only deletes, but will ask me to confirm?

I like having 'the trash'.  But I would rather have the ability to have confirmation of 'removing an item from a specific location' wether that be deleting or trashing. 

If nautilus had an 'undo' actions for when it trashs/moves files, then I don't having a confirmation wouldn't be necessary, but I would still like one.

Any ideas?

---

### Post by aysiu on 2005-12-04
[QUOTE=naked]
I like having 'the trash'.  But I would rather have the ability to have confirmation of 'removing an item from a specific location' wether that be deleting or trashing. [/QUOTE] This may be an extreme workaround, but you could try KDE. The behavior you're describing is the default in KDE.

---

### Post by manicka on 2005-12-05
[QUOTE=naked]Hum.  Is there a way to disable the 'trashing' so that it only deletes, but will ask me to confirm?
Any ideas?[/QUOTE]

You can add the delete option to the right click menu, but the trash option will remain there as well. Following aysiu's recommendation, maybe you could install konqueror and the associated kde files to see if you prefer that instead, before committing to a full kde install.

---

