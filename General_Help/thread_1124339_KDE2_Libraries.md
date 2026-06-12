---
title: "KDE2 Libraries"
date: 2009-04-13
forum: General Help
---

### Post by tcoffeep on 2009-04-13
A program that's been out of development for awhile requires KDE2 libraries, and doesn't register any compatibility with KDE4 or 3.5. I'm unsure of where I might find these libraries, or if a simple adjustment to the Makefile would fix it. Also, if I try to compile it by source, it complains about autoconf, stating that it's too high an upgrade or something.

The program I'm trying to install is xpertmud. Any ideas?

---

### Post by tcoffeep on 2009-04-13
I hate to bump this, but I'm really wondering if there is a way. I've tried looking, but nothing comes up.

---

### Post by tcoffeep on 2009-04-15
I guess by lack of response, getting KDE2 libraries are not even plausible?

---

### Post by getaceres on 2009-04-15
Maybe compiling from sources and them being careful of the location where you are installing them. One "simple" solution is to download KDE2 libraries (probably you will need QT2 as well) and then compiling and installing it to /opt to be sure you don't overwrite any QT4 or KDE4 file. Then you can compile your KDE2 application against this /opt environment.
It's not easy but I think it might be possible.

---

### Post by Ayuthia on 2009-04-15
Have you checked out this link:
[http://docs.btmux.com/index.php/Xpertmud:Getting_Started:Ubuntu_Guide](http://docs.btmux.com/index.php/Xpertmud:Getting_Started:Ubuntu_Guide)

I think that it is based on Hardy, but I would think that it should work about the same for Intrepid.

---

### Post by tcoffeep on 2009-04-15
I use Jaunty, but, I followed that thoroughly, and only got error messages, claiming the kde libraries weren't there. I installed the kde 3 libraries too, just in case, and nothing.

Also, I can't find any kde2 files. Even a google search shows more kde 4.2 when searching for kde2.

---

