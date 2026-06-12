---
title: "Cron troubles"
date: 2006-01-04
forum: Desktop Environments
---

### Post by joselin on 2006-01-04
Hi,

The cron saids me the following (or something like... with other symlinks) in the three machines with ubuntu i have own. Anyone can explain me why and how can i solve it?

```
/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink

```

Regards.

---

### Post by Cordate on 2006-01-04
According to [this page]("http://lists.debian.org/debian-user/2003/10/msg00546.html"), 
> 
A 'dangling symlink' is one whose target does not exist; a piece of
string with the weight cut off. Sometimes they are called 'hanging
symlinks' but 'dangling' is a better fit.

It looks like you'll need to find the current location(s) of the file(s) that the link is pointing to and correct the cron entry.

---

