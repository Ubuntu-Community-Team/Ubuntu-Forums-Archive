---
title: "Changing owner?"
date: 2009-02-26
forum: General Help
---

### Post by Gamak on 2009-02-26
k so yea, this is just an add on to my other topic. how do i change ownership of usr/share/themes folder. full code for terminal? please and thanks. :)

and then perhaps a wee code for extracting my theme to it? :D

---

### Post by dcstar on 2009-02-27
> **Gamak said:**
> k so yea, this is just an add on to my other topic. how do i change ownership of usr/share/themes folder. full code for terminal? please and thanks. :)

and then perhaps a wee code for extracting my theme to it? :D

You don't. Changing the setting of any system folder will most likely break you system.

If you want to copy something into it, you do it using the sudo command.

---

### Post by mb_webguy on 2009-02-27
The chown command is used to change the ownership of files and directories.The general syntax is:```
chown *user*:*group* *filename*
```To make it recursive (and change the ownership of all files and directories in a directory) you'd add the "-R" option after the command:```
chown -hR *user*:*group* *directory/*
```  (The "h" option prevents chown from following symbolic links, which is generally not what you want to do.)  You'd need to precede chown with sudo, of course, to change the ownership of files or directories owned by another user, such as root.

That said, dcstar is absolutely correct that you shouldn't change the ownership of system files.  This *will* break your system.

---

### Post by Gamak on 2009-02-27
yea thnx guys. i just done the... gksudo thunar and that file pops up and voila. thats easy, and fast, thnx guys :)

---

