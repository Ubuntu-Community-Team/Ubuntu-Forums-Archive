---
title: "[SOLVED] HELP! Hard drive space dissappearing"
date: 2009-01-12
forum: General Help
---

### Post by kaarnijoki on 2009-01-12
Hullo


Just managed to copy my music from old hard drive (thank you for help, Heindsight!). Moved some of it in the waste basket when running Nautilus as Root. Now. Cannot seem to access the waste basket to empty it? Everything i deleted as root seems to have stayed in root-wastebasket which for some reason is out of reach. When trying to access it i get : Sorry, could not display all the contents of "trash": Operation not supported

Any suggestions please?

Thank You

Use the force



Pasi

---

### Post by mcduck on 2009-01-12
Open the file manager as root (by running "gksudo nautilus"), browse to /root/.local/share/Trash/files and remove the files by selecting them and clicking shift-delete (to remove them immediately instead of moving to trash).

(the .local is a hidden directory, press Ctrl-H toggle visibility of hidden files/directories).

Alternatively, open a terminal and run following commands to empty root's trash:
```

sudo rm -r /root/.local/share/Trash/files/*
sudo rm -r /root/.local/share/Trash/info/*
```

---

### Post by cariboo on 2009-01-12
Start nautilus as root, press Alt-F2 and type:

```
gksu nautilus
```

Once nautilus has started press Ctrl-h to reveal the hidden files and directories. Navigate to .local/share/Trash and delete all the files in the files and info directories.

Jim

---

### Post by kaarnijoki on 2009-01-12
BIG THANK YOU for both of you.I was completely lost there. IVe only recently switched from Mac (well actually it was windows vista that finally did it. I was forced to use my wifes computer for a while after my well served Mac died) to the world of Linux. I cannot believe how much more you can do with Ubuntu and how well these forums work. 

Thank You again.

Love and lightning


Pasi

---

### Post by drs305 on 2009-01-12
Welcome to the ubuntu forums Pasi. 

Should you be interested in more about the ubuntu Trash system, how to find and delete it, as well as other ways to free up disk space, you can review this link: [http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

To mark a thread solved, please use the Thread Tools link near the top right of the first post. It assists others looking for solutions and allows helpers concentrate on unresolved issues.

---

### Post by kaarnijoki on 2009-01-12
Thank You. 


Will have a look at that.

This is fantastic. Everybody is so helpful here! 


Ubuntu rocks.


P

---

### Post by mcduck on 2009-01-12
Yes, Ubuntu's users seem to be more helpful than what you can expect on most computer-orientated forums..

Anyway, you might also be interested in Finnish Ubuntu forums: [http://forum.ubuntu-fi.org/]("http://forum.ubuntu-fi.org/").

While not as active as this international forum (what can you expect with 9000 users compared to 745000), people there are just helpful as here. And being able to ask questions in your native language is always nice.. ;)

---

