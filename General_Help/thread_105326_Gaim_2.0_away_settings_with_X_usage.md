---
title: "Gaim 2.0 away settings with X usage"
date: 2005-12-18
forum: General Help
---

### Post by cbudden on 2005-12-18
Hello.  I installed Gaim 2.0 beta1 last night and it is very good, however, it does not set away status by listening to X usage, but gaim usage which i don't want it to do.  How can I get it to compile and listen to X?
```
For packages that use the X Window System, `configure' can usually
find the X include and library files automatically, but if it doesn't,
you can use the `configure' options `--x-includes=DIR' and
`--x-libraries=DIR' to specify their locations
```

From the readme file.  What should i put in the DIR section?

Thanks very much.

PS. Here is the .deb I generated using checkinstall, it has spell checking and sound compiled with it.
[http://cbudden.sitesled.com/gaim-2.0.0beta_i386.deb](http://cbudden.sitesled.com/gaim-2.0.0beta_i386.deb)

---

### Post by cbudden on 2005-12-18
Anyone?

---

### Post by khc on 2005-12-18
Install libXext-dev

---

### Post by NunoCorreia on 2005-12-18
Good work on that package ;)

---

### Post by cbudden on 2005-12-19
[QUOTE=khc]Install libXext-dev[/QUOTE]

Hmm, apparently I already have it installed.

---

### Post by Karma_Police on 2005-12-20
Had that problem too, and I saw here how to solve it: [http://sourceforge.net/forum/forum.php?thread_id=1404993&forum_id=665](http://sourceforge.net/forum/forum.php?thread_id=1404993&forum_id=665)


install libxss-dev, or do a "sudo apt-get build-dep gaim". (but you only need libxss-dev).

I'm trying it right now

---

