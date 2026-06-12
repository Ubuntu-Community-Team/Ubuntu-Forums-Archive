---
title: "i messed up some things with libgio"
date: 2011-01-23
forum: Desktop Environments
---

### Post by amireldor on 2011-01-23
I have a similar problem as in [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1000129](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1000129) but I'm not sure how this guy solved it.

The problem is that when I try:
```
>>> gnome-open <url here>
Error showing url: Operation not supported

```I don't find any relevant libgio or gio packages in aptitude. I also tried to compile and install `gio` from the GNOME git repositories but I think it's not related at all :)

I suppose this gnome-open thing is used to open URL's in pidgin and open the help menu when pressing F1 in a terminal window for example, as both of these actions does not work (this is after I played around with some packages).

---

### Post by amireldor on 2011-01-31
well, I'm not sure what I did, but the bad things happened after I  played around with compiling and installing all kinds of GNOME packages,  with glib being one of them.

After searching some stuff on the  net I found out that when I run buggy programs with LD_LIBRARY_PATH set  to /usr/lib instead of /usr/local/lib then things worked.
I guess the new glib stuff were installed to /usr/local/lib and the older glib version stayed on /usr/lib.

Anyway  things work now, sort of, but I'm still not sure if the new glib I  needed to compile things with will work or what I'll do with it. I'm  clueless! All I wanted is to compile evolution!

P.S.
The things started to work after I prepend the line "/usr/bin" before "/usr/local/bin" in the file /etc/ld.so.conf.d/libc.conf

---

