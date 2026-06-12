---
title: "Help w/ The Mana World"
date: 2005-11-12
forum: Gaming &amp; Leisure
---

### Post by isaacf on 2005-11-12
I just installed the Debain package for The Mana World ([http://themanaworld.org/]("http://themanaworld.org/")) and it won't run. I have the icon in the games menu, and apt-get didn't give me any errors when installing, but whenever I run it nothing happens. Any thoughts?

---

### Post by Brandon14u2 on 2005-11-12
Have you tried running it through the terminal.  Maybe under sudo.  If it works with sudo you may need to change the permissions.


Just take my advice with a grain of salt, very much a newbie.

---

### Post by isaacf on 2005-11-12
I ran it in the command line and it gave me this error.

> 
tmw: error while loading shared libraries: libssl.so.0.9.8: cannot open shared object file: No such file or directory


---

### Post by Perfect Storm on 2005-11-12
Ubuntu have only version 0.9.7 availble.

---

### Post by lateo on 2005-11-12
this game looks good :-)
hope it will work soon! (with deb package)

has anyone tried from source? maybe the required lib is provided?

---

### Post by xsence on 2005-11-17
[QUOTE=lateo]this game looks good :-)
hope it will work soon! (with deb package)

has anyone tried from source? maybe the required lib is provided?[/QUOTE]

i love playing 2d games like snes en gba etc but not on my pc :)

but it look great

---

### Post by Bjørn on 2005-11-17
[QUOTE=Artificial Intelligence]Ubuntu have only version 0.9.7 availble.[/QUOTE]
Indeed, even though we fail to note this on the website at the moment, the apt repository of [The Mana World](http://themanaworld.org) currently only works for Debian testing or unstable (Etch or Sid).

One option is to compile [Guichan](http://guichan.sourceforge.net/) and The Mana World yourself, see [this thread](http://ubuntuforums.org/showthread.php?t=86041) for a bit of trouble shooting.

What I forgot to note there is that you'll encounter problems when compiling Guichan with GCC 4 because of a warning in combination with the -Werror option. See [this forum thread](http://guichan.sourceforge.net/forum/read.php?3,335) for the small modification required to the Guichan source.

---

