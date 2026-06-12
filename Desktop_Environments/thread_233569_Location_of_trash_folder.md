---
title: "Location of trash folder"
date: 2006-08-10
forum: Desktop Environments
---

### Post by mgc1952 on 2006-08-10
Hi - I am assuming that somewhere there is a folder which is represented by the trash appplet on the panel. Does anyone know where it is located?

Thank you
Mark

---

### Post by FeestBijtje on 2006-08-10
Username trash dir is: /ghome/<name>/.Trash/ (its a hidden dir)
Root trash dir is: /root/.Trash/

If you delete them both then files are deleted directly if you press delete or do an rm command.

Greets FeestBijtje

---

### Post by The Seeker on 2006-08-10
Whilst you're in your Home folder, hit Ctrl+H and you'll see a bunch of hidden folders, .Trash being one of them.

---

### Post by sumek on 2008-04-18
In Hardy Heron the location of Thrash folder is:
~/.local/share/Trash/

---

### Post by Mahyar on 2008-05-03
Thanks Sumek.  I was having trouble locating it.

---

### Post by ledenjes on 2008-06-26
> **Mahyar said:**
> Thanks Sumek.  I was having trouble locating it.

The EXACT location is: /home/<username>/.local/share/Trash/files

In order to succesfully delete all files (since 'cause of a bug in Ubuntu Hardy Heron, the trash bin cannot be emptied in the normal way), go to the gnome terminal and type: "*****" (without the quotes). This will delete ALL files AND folders AT ONCE.

There is also the folder /home/<username>/.local/share/Trash/info

In this folder, the trash bin stores its information (these are the folders which you will see in the gui trash bin). The files in this folder can easily be deleted.

Cheers.
:guitar:

---

