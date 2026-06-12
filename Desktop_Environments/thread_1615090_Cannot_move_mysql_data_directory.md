---
title: "Cannot move mysql data directory"
date: 2010-11-06
forum: Desktop Environments
---

### Post by crong on 2010-11-06
Ubuntu 10.04. I've tried every method I can find and none work. Here's what I know...

1. My /etc/my.cnf is ignored. I can even delete it and phpmyadmin continues to work as it did before.

2. If I move /var/lib/mysql and replace it with a new directory (chowned to mysql:mysql so it looks like it's got the same ownership & permissions as the original) I get a write permission problem, e.g.
> #1 - Can't create/write to file '/var/lib/mysql/test13/t13.MYI' (Errcode: 2)What I ultimately want to do is used existing database files on a FAT32 partition but I can't even get to first base. I'm stumped.

---

### Post by crong on 2010-11-07
I found that symlinking the individual database directories to '/var/lib/mysql/ worked and that was enough of a solution for me.

But I've just upgraded to 10.10 and it no longer works: The databases still get listed but they contain no tables.

This is my 5th unresolved post in this forum and I'm getting very discouraged.

---

### Post by frank.s on 2011-01-23
[Maybe you can find some help (click) here.]("http://www.ubuntugeek.com/how-to-change-the-mysql-data-default-directory.html")

Regards

---

