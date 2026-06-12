---
title: "libXrender.la ?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by vaskark on 2006-08-17
I've been getting this same message whenever I try to compile apps:

/bin/sed: can't read /usr/lib/libXrender.la: No such file or directory
libtool: link: `/usr/lib/libXrender.la' is not a valid libtool archive

This has just happened today. Is anyone else seeing this? I did a search for libXrender.la at [packages.ubuntu.com]("http://packages.ubuntu.com/") but nothing turned up.
](*,)

---

### Post by vaskark on 2006-08-18
*bump* anyone?

---

### Post by lazyd2 on 2006-08-18
Same here....

Anyone?

---

### Post by nacre on 2006-08-19
Are you using the QuinnStorm's repository?
If yes, then open /usr/lib/libcairo.la, and change the 17th line to:
dependency_libs=' /usr/lib/libfreetype.la -lz -lfontconfig -lpng12 -lXrender -lSM -lICE -lX11 -lm'

---

### Post by Cable on 2006-08-19
> **nacre said:**
> Are you using the QuinnStorm's repository?
If yes, then open /usr/lib/libcairo.la, and change the 17th line to:
dependency_libs=' /usr/lib/libfreetype.la -lz -lfontconfig -lpng12 -lXrender -lSM -lICE -lX11 -lm'
Mine looks like this...
```

dependency_libs=' /usr/lib/libfreetype.la -lz -lfontconfig /usr/lib/libglitz.la -lpng12 /usr/lib/libXrender.la -lSM -lICE -L/usr/X11R6/lib -lX11 -lm'

```
It has libXrender.la in it, but I still get the error.  Should I still change it to what you suggested?

---

### Post by mlind on 2006-08-19
btw. you can use handy tool called **apt-file** to search the package which provides /usr/lib/libXrender.la (if any).

---

### Post by vaskark on 2006-08-19
> **nacre said:**
> Are you using the QuinnStorm's repository?
If yes, then open /usr/lib/libcairo.la, and change the 17th line to:
dependency_libs=' /usr/lib/libfreetype.la -lz -lfontconfig -lpng12 -lXrender -lSM -lICE -lX11 -lm'

Yes, I am using that repo. I made the change and it seems to have worked! So many thanks to you, kind sir.

Anyone else who made the change and found that it didn't work: run 'make clean' inside your app's source directory before trying to compile again. I had to do that ;)

-- vaskark

---

### Post by lazyd2 on 2006-08-19
> **nacre said:**
> Are you using the QuinnStorm's repository?
If yes, then open /usr/lib/libcairo.la, and change the 17th line to:
dependency_libs=' /usr/lib/libfreetype.la -lz -lfontconfig -lpng12 -lXrender -lSM -lICE -lX11 -lm'
It works, thanks!

---

### Post by ChaKy on 2006-08-19
> **nacre said:**
> Are you using the QuinnStorm's repository?
If yes, then open /usr/lib/libcairo.la, and change the 17th line to:
dependency_libs=' /usr/lib/libfreetype.la -lz -lfontconfig -lpng12 -lXrender -lSM -lICE -lX11 -lm'

Thank you for this. :)

---

### Post by idn on 2006-08-21
Thanks, the fix mention here also worked for me - thanks alot!

---

### Post by amr2205 on 2006-08-26
> **nacre said:**
> Are you using the QuinnStorm's repository?
If yes, then open /usr/lib/libcairo.la, and change the 17th line to:
dependency_libs=' /usr/lib/libfreetype.la -lz -lfontconfig -lpng12 -lXrender -lSM -lICE -lX11 -lm'

It works here too, Thank you! :mrgreen:

---

### Post by berteh on 2006-09-01
> **nacre said:**
> Are you using the QuinnStorm's repository?


Yes, I did once... for trying glx... and now I get lots of troubles because of this (lib-vte4 was broken, a.o). Is there any way for removing any package that comes from this repo in my current installation? I don't use glx anymore even if it was fun ;o)

---

### Post by Loffe_ on 2006-09-09
Wow!

This easy fix worked for me too.

Thanks mate!

---

### Post by jasutton on 2006-09-29
I'm compiling beryl on dapper, and this worked for me too. :)

---

### Post by endlesssnowfall on 2007-02-13
The fix provided above doesn't work for me, whenever I try to compile something I get this error:

> libtool: link: `/usr/lib/gcc/i486-linux-gnu/4.1.2//libXrender.la' is not a valid libtool archive


I can't compile anything at all...

---

