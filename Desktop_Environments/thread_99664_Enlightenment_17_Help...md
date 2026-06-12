---
title: "Enlightenment 17 Help.."
date: 2005-12-06
forum: Desktop Environments
---

### Post by windowsXuser on 2005-12-06
I am currently running kubuntu 5.10 with kde 3.5.  I have read good things about E17so i decided to look into it.  I did a step by step how to install E17 by putting it into my repositories.  Here is the link that i followed.

[http://www.ubuntuforums.org/showthread.php?t=79155&highlight=e17](http://www.ubuntuforums.org/showthread.php?t=79155&highlight=e17)

The only part of the how to i couldn't do was getting 
- Tool for configuring E17 with a gui Erme (Enlightenment_Remote Made Easy)
-E17 genmenu.

i wasnt sure how to do ERME and i got these errors when trying to install E17genmenu:

blair@windowsXuser:~/e17genmenu$ ./autogen.sh
Running aclocal...
aclocal: configure.in: 19: macro `AM_ENABLE_SHARED' not found in library
aclocal: configure.in: 20: macro `AM_PROG_LIBTOOL' not found in library
aclocal: configure.in: 87: macro `AM_PATH_GTK' not found in library

I have installed the following modules:
engage, eclair, elicit, entice , examine, evidence, eterm 

I couldn't get these modules, it said the package could not be found:
e-modules , e-utils

Is there any other packages i should be installing?

Finally, on my menu bar it doesnt display any programs, system tools, utilities, internet.  Is there something i have to do to show these in the menu bar like kde does?

I have been reading up on adding programs to engage (OSX style dock), is there an easier way to do this instead of tweaking the .order file?

Sorry for the long email, but any help would be appreciated.

blair..

---

### Post by lerrup on 2005-12-06
Now I will admit I don't know that much about this, but I think E17 won't run with KDE, but will with gnome.

Have you checked the how-tos?

---

### Post by windowsXuser on 2005-12-06
i have it installed over kde and works just fine.  its actually quite faster than kde for sure.

i was just having trouble customizing the menu bar and engage dock.
just wanted to make sure i have the correct modules installed.

blair.

---

### Post by bored2k on 2005-12-06
[QUOTE=windowsXuser]i have it installed over kde and works just fine.  its actually quite faster than kde for sure.

i was just having trouble customizing the menu bar and engage dock.
just wanted to make sure i have the correct modules installed.

blair.[/QUOTE]
e17genmenu is easily installed from source. [http://sourceforge.net/projects/e17genmenu](http://sourceforge.net/projects/e17genmenu)

and btw, i HIGHLY recommend you build from CVS. it's a lot more stable (from my experience) and usable. [http://www.ubuntuforums.org/showthread.php?t=97199&highlight=enlightenment](http://www.ubuntuforums.org/showthread.php?t=97199&highlight=enlightenment)

---

