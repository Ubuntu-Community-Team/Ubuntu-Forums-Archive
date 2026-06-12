---
title: "can't unlock machine, can switch user and login to session however..."
date: 2009-02-22
forum: General Help
---

### Post by uschxc on 2009-02-22
a while back i made a big boo boo on the command line by accidentally changing the group of a lot of files on my system from root to users.  i beleive i've reversed the command to for the most part, and upgrading to hardy heron reinstalled most of the files and my system works fine from appearance.

however whenever my screen saver kicks in or i lock the machine, i can't unlock it.  i can log into the account, and once the unlock screen is present, i can click switch users and just re-login into my session.  

currently /home has the following attributes

drwxr-xr-x   5 adam root  4096 2008-10-28 12:17 home

---

### Post by spiderbatdad on 2009-02-22
generally /home is root:root
/home/user is user:user

---

### Post by uschxc on 2009-02-23
i made that change after the post, and didn't resolve the issue.  hope i don't have to reinstall to fix this weird bug.

---

### Post by uschxc on 2009-02-25
bump

---

### Post by bodhi.zazen on 2009-02-25
> **uschxc said:**
> a while back i made a big boo boo on the command line by accidentally changing the group of a lot of files on my system from root to users.  i beleive i've reversed the command to for the most part, and upgrading to hardy heron reinstalled most of the files and my system works fine from appearance.

however whenever my screen saver kicks in or i lock the machine, i can't unlock it.  i can log into the account, and once the unlock screen is present, i can click switch users and just re-login into my session.  

currently /home has the following attributes

drwxr-xr-x   5 adam root  4096 2008-10-28 12:17 home

In general the best solution is to re-install. As you can see, although it may appear you fixed most things, you are still having errors. Resolving all these errors will often take longer then the time it takes to re-install.

---

### Post by uschxc on 2009-02-25
would the update to jaunty maybe fix it?  i figure the update will reset the permissions/owners on files...but maybe not?

if not and a re-install is the only way, i can't just install over my current one and keep my settings and such can i?  i've gotten pretty comfortable using linux/ubuntu but haven't had very much experience with installs and migrations.

---

### Post by bodhi.zazen on 2009-02-25
Well I doubt re-installing packages will fix your problem.

You can move home to it's own partition and your settings will be preserved.

Personally I use a /data partition , settings are easy to restore, but that is me and I keep my settings to a minimum.

---

