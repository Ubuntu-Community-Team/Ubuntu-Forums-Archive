---
title: "Installed sdlmame... need help now"
date: 2008-02-08
forum: Gaming &amp; Leisure
---

### Post by Zzzach on 2008-02-08
Ok I just installed sdlmame on 64-bit ubuntu. Now I don't know what to do. When I tried installing kxmame from the repositories it wanted to delete sdlmame! When I run sdlmame it just flashes a screen then closes and there are no help files or anything for it. So what do I do now? :confused:

---

### Post by DoktorSeven on 2008-02-08
You need the new SVN repository version of kxmame to be compatible with SDLmame.  I created a package for it here:
[http://sdcofer.googlepages.com/](http://sdcofer.googlepages.com/)

---

### Post by Zzzach on 2008-02-08
Will that one work with 64-bit ubuntu though? I wasn't sure.

---

### Post by DoktorSeven on 2008-02-08
I have no idea.  I only have 32-bit machines so that's all I can build.  You can certainly try but I can't guarantee it'd work at all.

You can follow the link beside it to the kxmame site (the proper download is "kxmame-2.0-svn-sdlmame-20070603.tar.bz2" on its sourceforge site) and try to build it yourself (you'll need build-essential and kde-devel (oops, kde-devel, not kde-dev, sorry) packages at the least, plus ./configure needs the --disable-joystick (disable joystick support for just for the GUI, not for sdlmame itself -- it seems to not want to compile with joystick support enabled) switch.

Edit: The source is in the "trunk" directory and you need to run **make -f Makefile.cvs** (from that directory) to create the "configure" script.

---

### Post by disturbedite on 2008-02-08
> **Zzzach said:**
> Will that one work with 64-bit ubuntu though? I wasn't sure.
no, obviously the 32bit version will not install on 64bit.  but there is a dpkg command to force the 32bit package to install:
```
dpkg --force-architecture -i /path/to/debpackage 
```

---

### Post by Zzzach on 2008-02-08
Oh alright thanks. I didn't know about that. I didn't think the 32 bit version would work.

---

### Post by Zzzach on 2008-02-08
dang ok I tried that force architecture thing and it did it but I'm getting an error when I try launching kxmame. I've never complied a program before (I'm pretty new to linux still).

edit: OK I'm still learning. I used getlibs and installed some files I needed and now it works! Thanks!! :D

---

### Post by Zzzach on 2008-02-08
Ok got everything working now I think!

---

### Post by disturbedite on 2008-02-09
sweet.  glad it worked for you.

i just heard about lincade.  i wonder if its like wahcade, which i hated....
anyone know what its like?

EDIT:
ah, it appears to a multi system frontend to multi system frontends... lol

---

