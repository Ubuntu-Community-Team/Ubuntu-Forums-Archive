---
title: "&quot;collect2: ld returned 1 exit status&quot; error when compiling with GCC"
date: 2008-12-24
forum: General Help
---

### Post by justrasputin on 2008-12-24
I've been working on the Euler problems ([http://projecteuler.net]("http://projecteuler.net")) but for some reason, I see the following when I try to compile anything involving the math.h header file, e.g.

```
rasputin@rasputin-laptop:~/Documents/euler/c$ gcc p012.c
/tmp/ccaN3FGJ.o: In function `main':
p012.c:(.text+0xa7): undefined reference to `sqrt'
collect2: ld returned 1 exit status
```

This happens with any function in math.h, and yes, I have written

```
#include <math.h>
```

math.h exists in /usr/share, and the other header files I've used (stdlib, stdio, string) are in there as well.

I can compile it by adding the -lm argument to link the math library, but I dislike having to do that.

I tried removing and reinstalling build-essentials, didn't help.

I've googled this for a while, all the solutions I found were simply adding the -lm tag, or using g++ (which, by the way, does not need the -lm argument).

If anyone could point me in the right direction, I'd appreciate it.

---

### Post by justrasputin on 2008-12-25
bump to top so maybe some wise ubuntu user might notice this and give some advice

:popcorn:

---

### Post by mc4man on 2008-12-25
Beyond my knowledge but while a 'slow' forum you may wish to repost here (be patient

[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

---

### Post by justrasputin on 2008-12-25
Thanks for the tip, I've reposted there.

---

### Post by igknighted on 2008-12-25
Did you install build-essential?  For some reason, Ubuntu's GCC doesn't work right away, I can't explain why.  But I've had that issue with simple C progs, and that did the trick.

---

### Post by justrasputin on 2008-12-25
> **igknighted said:**
> Did you install build-essential?  For some reason, Ubuntu's GCC doesn't work right away, I can't explain why.  But I've had that issue with simple C progs, and that did the trick.

see:

[QUOTE=justrasputin]I tried removing and reinstalling build-essentials, didn't help.[/QUOTE]

---

### Post by justrasputin on 2008-12-29
Last try :D BUMP, I haven't made much headway, has anyone seen this and made some headway in fixing it?

Or is it something obvious that I'm missing so nobody feels like typing it out?

---

### Post by snova on 2008-12-29
> **justrasputin said:**
> I can compile it by adding the -lm argument to link the math library, but I dislike having to do that.

Then you already have the solution. ;)

If you're looking for a way to get around linking in the math library, there isn't one.

sqrt() and the rest of the advanced math functions are located in the math library. And there they will remain...

---

