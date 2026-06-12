---
title: "Mathematica 6 &amp; Ubuntu 8.04"
date: 2009-01-11
forum: Education &amp; Science
---

### Post by minollo on 2009-01-11
Hi!
There are some known issues that make Mathematica 6 not running on Ubuntu 8.04? 
I installed it - apparently without problems - but when I run it ... all my X session crashes and I come back at the login screen!!!

Any help  is gratefully acknowledged. 
Thanks in advance.

---

### Post by mattyB on 2009-01-11
Are you running Mathematica via Wine or the Linux version?

---

### Post by minollo on 2009-01-11
> **mattyB said:**
> Are you running Mathematica via Wine or the Linux version?

No wine,  it's the linux version. 
The problem is related to the server X because the mathematica kernel (the "math" command) works.

---

### Post by stumbleUpon on 2009-01-11
> **minollo said:**
> Hi!
There are some known issues that make Mathematica 6 not running on Ubuntu 8.04? 
I installed it - apparently without problems - but when I run it ... all my X session crashes and I come back at the login screen!!!

Any help  is gratefully acknowledged. 
Thanks in advance.

Try 
```
mathematica -defaultvisual
```

instead of just mathematica at the terminal.

---

### Post by minollo on 2009-01-12
> **stumbleUpon said:**
> Try 
```
mathematica -defaultvisual
```

instead of just mathematica at the terminal.


I tried but unfortunately without any success! :(:(:(

---

### Post by Berto88 on 2009-01-20
You could try

```
 env XLIB_SKIP_ARGB_VISUALS=1 mathematica
```

---

### Post by minollo on 2009-01-22
Nothing! I get always the crash of the server X! :(



> **Berto88 said:**
> You could try

```
 env XLIB_SKIP_ARGB_VISUALS=1 mathematica
```

---

### Post by x3qt0r on 2010-07-26
Well this is about Mathematica 7 and ubuntu 10.04.

I installed it correctly as the Math command works .
But it did not work in GUI.
So I tried the  
```
env XLIB_SKIP_ARGB_VISUALS=1 mathematica
```
But it starts with a segmentation fault and works.

Do I always have to start it this way?

---

