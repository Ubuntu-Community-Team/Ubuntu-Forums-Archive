---
title: "sh command"
date: 2006-05-10
forum: Desktop Environments
---

### Post by frogotronic on 2006-05-10
Can I make an alias to "tcsh" for "sh" command?  Are they equivalent?

Thanks

---

### Post by kabus on 2006-05-10
Sh and tcsh use different syntax and therefore aren't equivalent, as far as I know.

---

### Post by gibson on 2006-05-10
[QUOTE=cement_head]Can I make an alias to "tcsh" for "sh" command?  Are they equivalent?

Thanks[/QUOTE]


Nope - they are different.

What do you want to do... there may be another solution rather than symlinking

---

### Post by frogotronic on 2006-05-11
[QUOTE=gibson]Nope - they are different.

What do you want to do... there may be another solution rather than symlinking[/QUOTE]


Hello,

I'm trying to get IMAGE from the Sanger center to work.  It's a programme that imports TIFF files.  I need to install the 'libtiff3g' library.

When I type:

>sudo apt-get install libtiff3g

I get the following error:

> E: Couldn't find package libtiff.so.3

Any suggestions?

Thanks

---

### Post by Ramses de Norre on 2006-05-11
```
apt-cache search libtiff
``` will reveal the available packages.

---

### Post by frogotronic on 2006-05-11
[QUOTE=Ramses de Norre]```
apt-cache search libtiff
``` will reveal the available packages.[/QUOTE]

Thanks.

I installed the libtiff.3.g library from the GNOME archive.

[URL=
http://packages.debian.org/oldstable/libs/libtiff3g
]http://packages.debian.org/oldstable/libs/libtiff3g[/URL]

sudo dpkg -i libtiff3g*.deb

The IMAGE program now works.

---

