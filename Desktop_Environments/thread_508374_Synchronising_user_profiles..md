---
title: "Synchronising user profiles."
date: 2007-07-24
forum: Desktop Environments
---

### Post by sirgeekalot on 2007-07-24
i'm currently running xubuntu on two laptops. 

i was wondering if there was any way to synchronise the two profiles so that passwords and desktop settings accross the two using a another server i have running ubuntu server on the internet?

its mainly so that my girlfriend doesn't bug me everytime she creates a new shortcut or changes her password.

even just the password bit would be a help, the rest i think she could live without.

---

### Post by pbcartwright on 2007-07-24
check out rsync. rsync is a good method of doing backups too. See "man rsync":
  rsync is a program that behaves in much the same way that rcp does, but
       has many more options and uses  the  rsync  remote-update  protocol  to
       greatly  speed  up  file  transfers  when the destination file is being
       updated.

       The rsync remote-update protocol allows rsync to transfer just the dif&#8208;
       ferences between two sets of files across the network connection, using
       an efficient  checksum-search  algorithm  described  in  the  technical
       report that accompanies this package.

---

