---
title: "Desktop Folder Deleted?"
date: 2006-04-01
forum: Desktop Environments
---

### Post by wik on 2006-04-01
Hi,

I was trying to format and mount an external hard drive and suddenly I realized that all my desktop files were deleted, I don't know why, I suspect something related to my trials to the mount/umount. Is there a log I can check out and see what happened ? and how can I do that ?

Can I retrieve my lost files ?

regards

---

### Post by Requiem on 2006-04-01
[QUOTE=wik]Hi,

I was trying to format and mount an external hard drive and suddenly I realized that all my desktop files were deleted, I don't know why, I suspect something related to my trials to the mount/umount. Is there a log I can check out and see what happened ? and how can I do that ?

Can I retrieve my lost files ?

regards[/QUOTE]

Lets see... In the menu:
Applications/System Tools/Configuration Editor

onse there look for this in the tree on the left
apps/nautilus/preferences
and see if show_desktop is 'on'

also in that window, there is a key named desktop_is_home_dir, is it on or off?

Go to your Home folder and tell me if you still have a 'Desktop' folder.

It would be good to check if your files ended in '/lost+found' (look in your root dir)
run gconf and go to the nautilus

---

### Post by wik on 2006-04-01
show_desktop is on
desktop_is_home is not on
i have a desktop folder but it is empty
i have checked and there are no files in /lost+found

I suspect that at one point I mistakenly executed : rm -rf * on my home directory, but I stopped it using ctrl-Z and then checked my files in the trash and restored them, however my files from the desktop weren't in the trash they were gone for good. I don't know why. Might that be the reason ?

If it is. Is there in UBUNTU like a sort of log of commands that u executed and the affected files. and why this happened like rm -rf should move the files to the trash.

regards

---

### Post by Ramses de Norre on 2006-04-01
rm doesn't move anything to trash, that's why you always need to be careful on using it. Files deleted by rm are gone forever..

---

### Post by taurus on 2006-04-01
That's why you want to run it with the i option for interactive, asking you again if you're sure...  I have this line in my ~/.bashrc so everytime I use an rm, it asks me to confirm it with a y for yes or n for no.
```

rm='rm -i'

```

---

### Post by Ramses de Norre on 2006-04-02
But that gets pretty annoying when you need to delete a large amount of files..

---

### Post by Hairy_Palms on 2006-04-02
mine did this once, i rebooted and the default 3 reappeared  (computer,Documents,Wastebasket) but the rest i had to drag down again from the applications menu

---

### Post by taurus on 2006-04-02
[QUOTE=Ramses de Norre]But that gets pretty annoying when you need to delete a large amount of files..[/QUOTE]
Then you just unalias it or use the -rf options!!!  ;) 
```

unalias rm
rm *
-or-
rm -rf *

```

---

