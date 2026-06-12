---
title: "Which file contains PATH?"
date: 2005-07-19
forum: Desktop Environments
---

### Post by jsmidt on 2005-07-19
I am new to linux.  I want to edit the PATH but I don't know which file it is in.  One website said in .bash_profile but I can't seem to locate that file.  Any help would be enjoyed. :grin:

---

### Post by art on 2005-07-19
[QUOTE=jsmidt]I am new to linux.  I want to edit the PATH but I don't know which file it is in.  One website said in .bash_profile but I can't seem to locate that file.  Any help would be enjoyed. :grin:[/QUOTE]
 Type cd (to go to your home directory), then gedit .bash_profile, or gedit .bashrc. With the dot in front of it!

---

### Post by dataw0lf on 2005-07-19
Alternatively, if you want the path to persist across users, edit /etc/profile

---

### Post by ebrowne on 2005-07-19
For new users this file may or may not exists if you want to change the path golbally for all users on the system you may want to take a look at /etc/profile

---

### Post by jsmidt on 2005-07-19
Thank you all for your help. :)

---

