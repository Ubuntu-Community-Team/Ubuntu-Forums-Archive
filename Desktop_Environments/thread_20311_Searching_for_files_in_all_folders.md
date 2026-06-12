---
title: "Searching for files in all folders"
date: 2005-03-16
forum: Desktop Environments
---

### Post by jasplund on 2005-03-16
When I try to search for a file in "Computer--> Search for file" I can only search for files in one folder at the time. While using SuSE 9.2 with GNOME 2.6 I just chose the folder "/" and then It searched in all folders

---

### Post by iomicifikko on 2005-03-16
[QUOTE=jasplund]When I try to search for a file in "Computer--> Search for file" I can only search for files in one folder at the time. While using SuSE 9.2 with GNOME 2.6 I just chose the folder "/" and then It searched in all folders[/QUOTE]
 ---> im a newbie <----

open a console and with root privileges or typing "sudo" before the othewr commands type:

find / -name string_u_are_searching

about "/" it will start from here and all subdirs
about "-name" u are serching in the name of files

ps: i usually use "*" character, for example to find any file or dir with  "ciao" in the name:

$sudo find / -name *ciao*    or
#find / -name *ciao*


ciao!;)

---

### Post by adun on 2005-03-16
slocate is an alternative. use "man slocate" to learn how to build the index.



/Ride on

---

### Post by alastair on 2005-03-16
I tend to use "find" on the command line - but looking at the GUI tool, it appears that "filesystem" is equivalent to "/" (root filesystem). Selecting "other options" lets you also recurse down other filesystems under root.

---

