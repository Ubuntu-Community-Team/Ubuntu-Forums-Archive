---
title: "Conform actions in Nautilus (move, delete, etc)"
date: 2006-09-29
forum: Desktop Environments
---

### Post by dannyboy79 on 2006-09-29
Can someone please inform me how to setup Nautilus so that if I enter it using gksudo or even normally that I can have it so a dialog box will appear for whatever action I perform and it'll ask me to confirm the action. For example, I went into Nautilus with gksudo to modify some folders in my ftp folder and all of a sudden my mouse went nuts and I moved a folder from the ftp folder to my home directory. I if didn't notice it wouldv'e sucked that my customers wouldn't have been able to get there stuff from my ftp server cause I accidentally moved it. Hopefully this is possible. Whether I do a move or a delete I would like a box to appear saying, are you sure. or something like that. thanks to whoever can help!

---

### Post by aysiu on 2006-09-29
You can have it warn you for a delete, but not for a move.

Go to Edit > Preferences > Behavior > Ask before emptying trash or deleting files

---

### Post by dannyboy79 on 2006-09-30
Nope, at least in Xubuntu within Thunar there is nothing like that within edit preferences. I can't believe I can't somehow set this up.

---

### Post by aysiu on 2006-09-30
Nope--nothing like that in Thunar.

You can, however, create a "move to trash" command in the context menu. Go to Edit > Configure Custom Actions > + > ```
mv %N ~/.Trash
``` for the command. Make sure you create the trash can first: ```
mkdir ~/.Trash
```

---

### Post by dannyboy79 on 2006-10-01
i don't need to do that because I have installed Thunar 0.4.0rc1. it has the trash built in, its awesome. it installed great also. they even have a graphical installer.

---

