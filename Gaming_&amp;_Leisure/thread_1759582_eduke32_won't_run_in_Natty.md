---
title: "eduke32 won't run in Natty"
date: 2011-05-15
forum: Gaming &amp; Leisure
---

### Post by cackerso on 2011-05-15
I added the repositories for eduke32 to KPackageKit and installed eduke32.  I have two small problems.  if I try ./usr/games/eduke32 I get the error "Segmentation fault".  If I  use sudo ./usr/games/eduke32, it will run.  Also trying the Kmenu entry won't start it either.

Should I park the executable somewhere else and change the permissions to mine?

Thanks,

cackerso

---

### Post by cackerso on 2011-05-27
Maybe the moderators could move this post to a more appropriate section of the forums since I haven't gotten a reply here in the games part.

Thanks,

cackerso

---

### Post by Brebs on 2011-06-02
Games are never meant to be run as root. So don't do it. Beginners will often try it, then maybe get a file written with root-only permissions in their $HOME, which they can't alter as their normal user, which only serves to confuse them even further.

Your command-line is bizarre. It should simply be:

eduke32

Try compiling [http://dukeworld.duke4.net/eduke32/synthesis/20110529-1900/eduke32_src_20110529-1900.tar.bz2](http://dukeworld.duke4.net/eduke32/synthesis/20110529-1900/eduke32_src_20110529-1900.tar.bz2) - it works for me. [Instructions](http://wiki.eduke32.com/wiki/Building_EDuke32_on_Linux).

---

### Post by cackerso on 2011-06-03
Thank you for the reply.  It is bizarre.  If it ran simply as eduke32 then I wouldn't have tried any thing else.  I was just trying to figure out what is wrong.  I deleted the whole thing and reinstalled it and it still won't run unless it's as root.  I also un-installed it and tried what you suggested and compiled it.  It works the same way.  Perhaps it has something to do with the fact that my home partition is encrypted.  I don't know.  It is interesting that other GTK+ programs like GIMP have the same problem in my install.  I'm not exactly where to to from here.  Perhaps it's a bug in Ubuntu.

cackerso

---

### Post by cackerso on 2011-06-29
Just in case this is a problem for anyone else.  This bug also affects GIMP the same way.  Anyway one fix, which was posted on another forum is;  change the widget for the desktop style form "Oxygen-GTK" to "Oxygen-molecule".  Compiling eduke32 in various configurations either didn't solve the problem or in some cases created new ones.

cackerso

---

