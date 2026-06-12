---
title: "How do you add a source install to package manager?"
date: 2005-10-25
forum: Desktop Environments
---

### Post by malacoda on 2005-10-25
Salut,

Question: how do you add or link an app that has been downloaded from source to your package manager - e.g. Adept in Kubuntu Breezy - so that any future Adept package installations are aware of it and play nice with it?

I saw a simple line or 2 of commands in a past thread that did this but I can't find the thread.

My particular example: I've had better success in Breezy with a source download of the nVidia drivers and the latest Superkaramba version.  But, since my package manager doesn't 'realize' I've done this I've had another app installed through package manager cause conflict with one of them...

Any simple explanation - e.g. clear enough for a noob to follow - of how to do this would be very much appreciated.

Stay sane or the crazies will get ya,
Malac

---

### Post by cwaldbieser on 2005-10-25
[QUOTE=malacoda]Salut,

Question: how do you add or link an app that has been downloaded from source to your package manager - e.g. Adept in Kubuntu Breezy - so that any future Adept package installations are aware of it and play nice with it?

I saw a simple line or 2 of commands in a past thread that did this but I can't find the thread.

My particular example: I've had better success in Breezy with a source download of the nVidia drivers and the latest Superkaramba version.  But, since my package manager doesn't 'realize' I've done this I've had another app installed through package manager cause conflict with one of them...

Any simple explanation - e.g. clear enough for a noob to follow - of how to do this would be very much appreciated.

Stay sane or the crazies will get ya,
Malac[/QUOTE]
If you get the "checkinstall" program, it can build your programs from source for you and create a .deb file that the package manager understands.  You unpack the .tgz archive, cd into the folder, and then:
```

$ ./configure
$ make
$ sudo checkinstall -D

```
There are some prompts you need to answer, I think.

---

