---
title: "find doesn't find my new files. How to update the find / search tools index ?"
date: 2009-04-26
forum: General Help
---

### Post by planetLars on 2009-04-26
Hi,

find doesn't find my new files. I know it happened in Hardy Heron where
the index needed updating before every search to find new files.

I guess this is the same problem here. But I don't remember the bash
command!!

Googling finds millions of pages relating to update manager and what else
completely different from my search term "ubuntu update find index".

I know it may already be answered somewhere on the internet as that's
where I probably got it from three quarters of a year ago but can you
help me still?

Thank you!!


Lars

---

### Post by nikgare on 2009-04-26
would this help:

**sudu updatedb**

---

### Post by Dr_Willis on 2009-04-26
**sudo updatedb**

updates the database for the **locate** command.
the database is also auto updated about once a day as a cron job.


**find** is used in about the same  way but different cases.


for example. I want to track down where the 'vimrc' file is at.

willis@cow:~/bin$ **locate vimrc**
/etc/vim/gvimrc
/etc/vim/vimrc
/etc/vim/vimrc.tiny
/usr/share/vim/gvimrc
/usr/share/vim/vimrc
/usr/share/vim/vimrc.tiny
/usr/share/vim/vim72/gvimrc_example.vim
/usr/share/vim/vim72/vimrc_example.vim


BUT if i want to 'find' all files or directories with other criteria i can use **find**.


Example - find all 'directories' and chmod them to be executable.

**find -type d -print0 | xargs -0 chmod 755**

find all files and fix the permissions on them to NOT be executable.

[B]  
find -type f -print0 | xargs -0 chmod 664 [/B]


both tools are similer  in some ways and radically differnt in others.



In answer to your actual 'topic'
 
 find SHOULD find/print all files that exist. it does not use the locate database, it reads the directory/file listing same as other commands like ls does.



Locate - uses database
find   - does not.

---

### Post by planetLars on 2009-04-26
Thank yous for your (comprehensive) answers. Very much appreciated. I'll
try sudo updatedb to see whether it makes a difference. Trying to
remember a bit more, this may have been the command I used to use :-)

In fact I was lazily referring to the gnome-search-tool accessible from
the default Ubuntu menus. Its help states it uses locate, find and grep.

Your help was and can be useful too!

Thanks!!

Lars

---

