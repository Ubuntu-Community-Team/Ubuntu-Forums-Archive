---
title: "Setting The PATH Environment Variable"
date: 2009-06-16
forum: General Help
---

### Post by chandu73 on 2009-06-16
Hi,

i have to set environment path to include some libraries to compile uclinux distribution. i copied the uclinux in my " /home/chandu " and the cross compiler in " /opt/bin and  edited the file ~/.bashrc file in my home directory.

i tested it with command "echo $PATH " and  get the included path.

but when i compile uclinux it's not finding the path what i mentioned, 

did am doing correct path setting or any wrong??

in my previous post some one told to edit ~/.profile , but if i do so am not getting any result when i give echo $PATH command.

pls help me 

Regards
Chandu

---

### Post by ad_267 on 2009-06-16
The compiler doesn't look for libraries in PATH, it looks in LD_LIBRARY_PATH.

---

