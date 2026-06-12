---
title: "$PATH question"
date: 2005-08-21
forum: Desktop Environments
---

### Post by s_p_a_r_k_y on 2005-08-21
is there a place to set the local path. Most distributions do so in .profile or .bashrc but I didn't see the $path variable being set in either of those file. I see its in /etc/profile but I don't want it for every user...should I put modify my own bash.rc or .profile?

if so would it be 
PATH = $PATH:~/bin/
to add my local bin folder?

---

### Post by nad on 2005-08-21
No spaces. Modify .bashrc if you wish all new terminals to use your new PATH.

PATH="${PATH}":~/bin

---

