---
title: "users-admin bug?"
date: 2008-02-13
forum: Desktop Environments
---

### Post by iris-n on 2008-02-13
I have this weird problem in users-admin, i'm reporting it here to certify it's a bug before listing it on launchpad.

The thing is, in a fresh install of 7.10 in an AMD Athlon XP computer, i went adding users for all. They all added fine (at least when added in the GUI) but, none showed up in the users-admin screen.

After a little research, i found out that somehow the values of UID_MIN and UID_MAX in the /etc/login.defs were set to zero. After setting them to 1000 and 10000, respectively (i'd be glad if anyone could inform me of the default values) all users appeared there, fine.

Has anyone else encountered this problem? Is it a bug or i inadvertently caused it myself?
A search about it on launchpad returned nothing.

Thanks in advance,

Iris

---

### Post by nemilar on 2008-02-13
From my /etc/login.defs file:

```

#
# Min/max values for automatic uid selection in useradd
#
UID_MIN                  1000
UID_MAX                 60000

```

As far as I know, these are the default values - which is to say, I've never modified that file.  But this install is about a year old, so YMMV.

---

### Post by iris-n on 2008-02-14
Hmm thanks.
Guess i'll have to reinstall in order to confirm it's a bug.

---

