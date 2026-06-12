---
title: "create new file -&gt; set permission to 777 and iso-8859-1"
date: 2005-05-26
forum: Desktop Environments
---

### Post by dabear on 2005-05-26
Hi, I am the only user on my toshiba laptop, where I also run an apache test server. Now since I use letters not in utf8, I want all subfiles and directories to use the file-encoding  iso-8859-1 and I also want to set all new files to 777. How do I do this autmatically when new files are created inside(or in a sub-dir) of /var/www ?

---

### Post by Alexander Kirillov on 2005-05-26
[QUOTE=dabear]Hi, I am the only user on my toshiba laptop, where I also run an apache test server. Now since I use letters not in utf8, I want all subfiles and directories to use the file-encoding  iso-8859-1 and I also want to set all new files to 777. How do I do this autmatically when new files are created inside(or in a sub-dir) of /var/www ?[/QUOTE]
 to change your sytem locale see 
[http://www.ubuntulinux.org/wiki/LocaleConf](http://www.ubuntulinux.org/wiki/LocaleConf)

For permissions - there is a way to set default permissions on *all* newly created file, by using umask command in .bash_profile. I do not know any way to make it per-directory

---

