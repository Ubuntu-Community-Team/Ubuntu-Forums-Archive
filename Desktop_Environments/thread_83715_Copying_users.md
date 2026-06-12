---
title: "Copying users"
date: 2005-10-29
forum: Desktop Environments
---

### Post by mokeyjoe on 2005-10-29
Is it at all possible to copy a user and all their settings to a new user name? I've got a couple of new users to add but don't want to have have to fiddle with all the settings all over again.

Just being able to copy all the settings would be fine.

---

### Post by swerner on 2005-10-29
See 'man adduser', this will talk about skeleton user files.  Basically you add the files that you want the new user to have into /etc/skel.  One thing be weary of is when you copy directories such as /home/username/.gconf/, /home/username/.gnome/, etc.  There may be some internal naming system that does not allow these configuration directories to be copied just like that.  But give it a go and see how it works.

---

