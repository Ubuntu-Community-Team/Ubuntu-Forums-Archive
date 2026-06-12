---
title: "Compiling, ./configure --prefix=/usr , works, but why?"
date: 2006-01-03
forum: General Help
---

### Post by brynjarh on 2006-01-03
I noticed when I compile software that it goes into /usr/local/ while everything I install from the repository goes into /usr/.

I didn't mind it much since I have little idea how the directories work until I tried compiling [The Mana World]("http://themanaworld.org/") on Ubuntu.

Now TMW requires [Guichan]("http://guichan.sourceforge.net/") which is not available in the repository, so I compiled that first and it went into /usr/local/ , then I try to compile TMW which doesn't work since it looks for Guichan in /usr/ (/usr/lib/libguichan*) like all other software on Ubuntu I guess?

So I remove Guichan and install it again but using "./configure --prefix=/usr" instead of "./configure", and then do the same to TMW, now everything works.

My question is what am I doing exactly?
Should I always use this prefix when compiling stuff on Ubuntu?
If not then in what cases should I do it and why?
And is there another way of getting this to work, is it better?

~A happy Ubuntu TMW player!

---

### Post by thessem on 2006-01-03
I'm pretty sure that "prefix" just tells the program where to install itself, and the default for your system is /usr/local/, but you tell it to install into just /usr/, and hence, it works.

---

### Post by sargek on 2006-01-04
By default, all software (in all distros) is installed in /usr, if you use the package management for your distro. There are some exception, like KDE on Suse, for example, goes into /opt. When you compile on your own and do not specify an installation directory to the configure routine, the software goes into /usr/local. This is by design. I believe this is done so user installed software is not be "mixed" with system software. There should be absolutely nothing wrong with this, as /usr/local should be in the user's path.

---

### Post by Suger on 2006-01-04
Yes, basically, /usr and /usr/local are used to keep separated distro files (/usr) from user installed files (/usr/local). Packages are seen as user installed files in BSDs and as distro files in most of the linuxs I know of. But that is just a general rule. You're on linux, it's your computer, you're free to install a given program wherever you want (be it in /not/here/but/there if it so pleases you), as long as the directory is in your PATH. The only risk you have in installing in /usr and not in /usr/local is to overwrite a distro installed library (or program) with one from the new program, which could put your system stability at risk.

---

