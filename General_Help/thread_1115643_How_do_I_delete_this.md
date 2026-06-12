---
title: "How do I delete this?"
date: 2009-04-04
forum: General Help
---

### Post by crispeto on 2009-04-04
I was going to make a backup of my drive when I realized it was backing up a wubi install so it wanted to back up all of my windows stuff too. I canceled the backup and it left me with a 2.7 gig icon named Backup.tgz in "file system". Since I can't simply right click and choose "move to trash", how do I delete it? Thanks.

---

### Post by evilaim on 2009-04-04
Well, you might have to do a forceful delete, depending.  So, try: sudo rm -f blah.tar.gz

---

### Post by jms1989 on 2009-04-04
I'm gonna take a guess and say that the file is owned by root and is stored in the root directory of your system, aka (/). Ok, simple.

All you need to do is use the root user to delete it but be forewarned, if you're not careful, you can mess your ubuntu install up.

Gui version:

1. Press Alt + F1. (This will bring up the run dialog.)
2. Type "gksu nautilus" (This will bring up a file browser under root.)
3. Navigate to the folder its stored in, click it and press Shift + Delete to remove it but skip the trash bin.
4. Done so close the file browser.

Terminal version:

1. Open the terminal. Applications -> Accessories -> Terminal
2. Type "sudo rm /Backup.tar.gz"
3. Hit enter and close.

Now, if the situation is different, please let up know. Cheers!

---

### Post by Elfy on 2009-04-04
If you're not completely sure of what rm -f /path you need to use you could possibly cause yourself some problems. You can also open naultilus with root rights 

```
gksudo nautilus
```

If you do use nautilus - then you will either need to make sure to empty root's trash before you leave or do Shift+Delete

---

### Post by crispeto on 2009-04-04
Yep, that did it! You all are good! Thanks for your help.

---

