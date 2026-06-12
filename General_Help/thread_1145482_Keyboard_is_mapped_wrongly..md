---
title: "Keyboard is mapped wrongly."
date: 2009-05-01
forum: General Help
---

### Post by fxckingscene on 2009-05-01
Hello,

Im quite a n00b when it comes to ubuntu so forgive me if i have posted this in the wrong section.

I have a microsoft wireless multimedia keyboard 1.1 and the keyboard is mapped wrongly within Ubuntu.

I have looked for the keyboard map and have found no solution and i am currently using 1.0A.

Im am running Ubuntu 9.04.

Does anyone have the solution?

Thank you in advance.

---

### Post by lensman3 on 2009-05-01
This is all handled in the X11 keyboard routines.  Do from a command line "man -k keyboard".  There are a lot of routines that map keys  and keyboards together.

Another suggestion is to look up how to map X11 to the Russian Cyrillic language.  There use to be a good FAQ on mapping to Russian.  In your case you just want to map the keyboard to "English".

---

