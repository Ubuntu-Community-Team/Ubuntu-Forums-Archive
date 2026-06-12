---
title: "error running juk"
date: 2005-10-06
forum: Desktop Environments
---

### Post by GameManK on 2005-10-06
i wanted to try JuK to compare to amaroK, but i get this error when trying to run it:

juk: error while loading shared libraries: libtag.so.1: cannot open shared object file: No such file or directory

I think it might be because I installed a new libtag version so i could use amarok 1.3

what can I do about this?

---

### Post by adwait on 2005-10-06
I am running breezy, and running juk fine. Normally, when such errors happen....I just rename the file to whatever the program wants and get on with it.....no idea if this correct or not, but usually it makes the program work. In this case, I would say run
```
locate libtag.so
```

You'll find that it is named something other that libtag.so.1.....try renaming it to libtag.so.1

---

### Post by Knome_fan on 2005-10-06
No, don't simply rename it, as this will probably break other programs, for example amarok.

As a dirty workaround you could of course try to make a symbolic link that reflects the version juk needs.

for example, in the directory where libtag.so* is located:
ln -s libtag.so.1.3 libtag.so.1

This might work.

Something else you could try is to rebuild juk against the new libtag.

---

### Post by GameManK on 2005-10-06
locate libtag.so
/usr/local/lib/libtag.so
/usr/local/lib/libtag.so.1.4.0
/usr/local/lib/libtag.so.1

looks like all the files/versions are there, so that's not the issue

---

### Post by Knome_fan on 2005-10-06
I think the problem is that you installed to /usr/local and /usr/local isn't in your PATH, so juk can't find it.

I really don't no what you installed and I can only urge you to be careful with simply installing stuff on your system without using proper package management, but anyway, either add /usr/local to your PATH, or make a symlink so that juk can find it:

ln -s /usr/local/lib/libtag.so.1 /usr/lib/libtag.so.1

---

