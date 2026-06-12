---
title: "Compiling qt4 fails"
date: 2005-11-26
forum: Desktop Environments
---

### Post by sabaoth on 2005-11-26
I tried to compile Qt 4.0.1 in my Kubuntu box and it fails when compiling the library libQtGui_debug.so.4

What I get is an error message when it tries to link all the .o objects to build the library. It exits and says: "collect2: ld returned exit status 1", BUT, however, there is no further information. All the libraries are in the path, and there is no missing symbol or whatever. I have run out of ideas, not even with the verbose option activated I get more information.

Someone else tried to build Qt 4.0.1 in breezy? Could then please paste here which gcc, stdlib, and automake versions were used when compiling?

---

### Post by sabaoth on 2005-11-26
Well, after I solved the problem, just a pair of things:

a) You guys, when compiling a big thing, you check you have enough FREE SPACE IN YOUR HARD DRIVE. (Jesus, I want to die).

b) Someone tell the people of the makefile thingy that hiding messages like "/usr/bin/ld: final link failed: there is not enough free space in the device" IS NOT A GOOD IDEA.

c) Someone please put a "you're running out of free space in your hard drive, so please free some before compiling such a big thing, you fool" big popup in Kubuntu, when compiling big things and running out of free space.

Jesus. Frustrating. Well, this two hours of my life are not completely worthless. At least people might laugh.

---

### Post by mmuggli on 2006-11-06
Thanks for posting the solution.  You just saved me a lot of ](*,)

---

