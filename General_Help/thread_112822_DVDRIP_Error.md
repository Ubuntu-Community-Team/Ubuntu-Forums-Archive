---
title: "DVD::RIP Error"
date: 2006-01-05
forum: General Help
---

### Post by Thanatos10 on 2006-01-05
When ever I try to use DVD::RIP I receive the following error:  mkdir/CHANGE_ME: Permission denied at /usr/share/perl5/Video/DVDRip/Project.pm line 261.  Has anyone else encounted this error and what was the fix?  I've serarched the web and I haven't been able to figure it out.  So any help would be appreciated.

---

### Post by schilcha on 2006-01-05
I don't have DVD::RIP, but from the error-message it seems that you (or the script) is trying to create the directory /CHANGE_ME. If you are not root, you certainly don't have the permission to create a dir in the directory-root. As the name suggests, you should (somewhere) change this directory to something like /tmp/dvdrip (if it's ok for you that the dir is removed during startup/shutdown -- i cant remember) or /home/yourusername/dvdrip or whatever.

Good Luck

---

### Post by kingsidy on 2006-01-05
start dvd:rip as root. like in the terminal type sudo dvdrip

---

### Post by yanik on 2006-01-05
go into preferences and change the path to something like /home/you/dvdrip or something.

---

### Post by Thanatos10 on 2006-01-06
Thanks for the input and sorry for the delay in responding, Being stationed in Japan kinda throws things off a bit.

Your suggestions worked great!  I simply went into the preferences and changed the default directories and all is well.

Thanks again for your time

---

