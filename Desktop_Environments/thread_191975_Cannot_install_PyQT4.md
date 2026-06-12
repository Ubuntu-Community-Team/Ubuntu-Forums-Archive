---
title: "Cannot install PyQT4"
date: 2006-06-08
forum: Desktop Environments
---

### Post by sjalv on 2006-06-08
I didn't know where to post this, thought I'd ask here first.

So, I've been trying to install PyQT4 for some time now, each time with different problems. I have finally made it to the make - make install part, but, again there were problems. make gives me these errors:

translator.cpp:22:27: error: qplatformdefs.h: No such file or directory
translator.cpp: In member function âbool Translator::load(const QString&, const QString&, const QString&, const QString&)â:
translator.cpp:425: error: âO_RDONLYâ was not declared in this scope
translator.cpp:431: error: âQT_OPENâ was not declared in this scope
translator.cpp:433: error: aggregate âstat stâ has incomplete type and cannot be defined
translator.cpp:434: error: âfstatâ was not declared in this scope
make[1]: *** [translator.o] Error 1
make[1]: Leaving directory `/home/hmyllyko/temp/sip/PyQt4-gpl-4.0beta1/pylupdate'
make: *** [all] Error 2

(my keyboard layout and locales are finnish, I think that's the reason the output has those â thingies in there :-k)

Naturally, make install fails too. Am I still missing some packages, or is there a bug in the make script or something? QT version is 4.1.2, Python is 2.4. Any help would be greatly appreciated.

---

