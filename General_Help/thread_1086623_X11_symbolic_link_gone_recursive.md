---
title: "X11 symbolic link gone recursive"
date: 2009-03-04
forum: General Help
---

### Post by oygle on 2009-03-04
Noticed in nautilus, when viewing /var/bin , the symbolic link X11 , when I open it, there is another X!!, then another X11, and another ????

Doing ' ls -al' on /usr/bin shows ..

lrwxrwxrwx  1 root   root          1 2002-01-01 13:55 X11 -> .

The date is not the same as nautilus, nautilus shows 'Wed 4th mar 21:30:20 EST'

What has happened to this symbolic link ?

Oygle

---

### Post by oygle on 2009-03-04
Is this the problem - [http://jetbrains.net/jira/browse/IDEA-11635](http://jetbrains.net/jira/browse/IDEA-11635)

Maybe there is no files to where the link points. If so, this is a bug.

---

### Post by oygle on 2009-06-16
Have upgraded to Jaunty, thought there might be a change in this problem, but it still exists. Doing an **ls** on /usr/bin shows

lrwxrwxrwx  1 root   root          1 2002-01-01 13:55 X11 -> .

the symbolic link called X11 is pointing up one level, and therefore continually shows the current path, which of course has the symbolic link X11 in it, and so it goes on and on.

Can this symbolic link be safely removed ??

Oygle

---

### Post by 3rdalbum on 2009-06-16
Isn't this normal? Every time I've looked, that's how /usr/bin/X11 is.

---

### Post by oygle on 2009-06-16
Why would a symbolic link point to the path it resides in ?

Surely this is an error.

---

### Post by CatKiller on 2009-06-16
It's normal. X's executables used to be in /usr/bin/X11. Now they are in /usr/bin. Some configurations need the files to be in the old location, so rather than have multiple copies of the same executable, which would be stupid, the old location is symlinked to the new location. Everything still works and everything is fine until, every now and then, someone says > OMG I'm in /usr/bin/X11/X11/X11/X11/X11/X11/X11/ !!!!!!111 It's been like it for quite some time.

---

### Post by oygle on 2009-06-17
> **CatKiller said:**
> It's normal........ Everything still works and everything is fine until, every now and then, someone says ..


OMG I'm in /usr/bin/X11/X11/X11/X11/X11/X11/X11/ !!!!!!111


Okay, thanks, I'll have to remember not to say that.  ;)

---

### Post by CatKiller on 2009-06-17
> **oygle said:**
> Okay, thanks, I'll have to remember not to say that.  ;)

It **is** a bit of a mouthful :)

---

