---
title: "Searching for files anywhere on HD"
date: 2005-10-27
forum: Desktop Environments
---

### Post by Kensi on 2005-10-27
The built in Places->Search for files feature is nice, but it only searches my home folder EVEN if I have selected to search the entire file system. How do i get search to work on my entire file system?

---

### Post by ubuntumaneh on 2005-10-27
A terminal solution, ok? 
Open a terminal, then use the command "locate"
Make a test: 

locate *.jpg

or 

locate "name of a file"

---

### Post by Kensi on 2005-10-27
Hmm, no luck


in /usr/local/games i have a quake4 folder, and in that there is a quake4 executable

locate quake4 or locate *quake4* or locate "quake4" returns nothing

---

### Post by Abandon on 2005-10-27
[QUOTE=Kensi]Hmm, no luck


in /usr/local/games i have a quake4 folder, and in that there is a quake4 executable

locate quake4 or locate *quake4* or locate "quake4" returns nothing[/QUOTE]

Try first the command: updatedb

---

### Post by ubuntumaneh on 2005-10-27
Try slocate, instead.

slocate quake4

---

### Post by RoyCowboy on 2005-10-27
```

find / -name "pattern"

```

..where pattern would be quake4

---

### Post by Zeroedout on 2005-10-27
if you want to use locate, first you have to make sure the database is up to date with all the new stuff you put in. To do this, type in sudo updatedb . We do this because as a user, you can't create a database in the location where it is stored, so if you want to update the database, you need to use sudo. Then when you do locate FILE , you will find all the new stuff since the last sudo updatedb. Hope this helped a little.

---

### Post by Kensi on 2005-10-27
[QUOTE=Zeroedout]if you want to use locate, first you have to make sure the database is up to date with all the new stuff you put in. To do this, type in sudo updatedb . We do this because as a user, you can't create a database in the location where it is stored, so if you want to update the database, you need to use sudo. Then when you do locate FILE , you will find all the new stuff since the last sudo updatedb. Hope this helped a little.[/QUOTE]

this worked, thanks

---

### Post by Kyral on 2005-10-27
Use Beagle :D

[http://www.ubuntuforums.org/showthread.php?t=78810](http://www.ubuntuforums.org/showthread.php?t=78810)

---

### Post by Kensi on 2005-10-28
[QUOTE=Kyral]Use Beagle :D

[http://www.ubuntuforums.org/showthread.php?t=78810](http://www.ubuntuforums.org/showthread.php?t=78810)[/QUOTE]

beagle works just as bad as the built in search without an updatedb

---

