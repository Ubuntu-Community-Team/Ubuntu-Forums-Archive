---
title: "Kernel Confusion??"
date: 2005-09-20
forum: Desktop Environments
---

### Post by bob_c_b on 2005-09-20
Okay, I added the i686 kernel to my Hoary install (as well as restricted 686 packages) and it went very smoothly and everything works great. But when I do a uname I get this...

```
Linux phobos 2.6.10-5-686 #1 Thu Sep 8 06:27:36 UTC 2005 i686 GNU/Linux
``` 

But when I look in Synaptic I see that the installed version is 2.6.10-7? Or am I not understanding the version #? Is this a patched kernel from the Ubunut devs or is something whacked? I want to add kernel headers but want to make sure I get the right version.

---

### Post by bob_c_b on 2005-09-21
I hate doing this but would really like to know, bump!

---

### Post by mlomker on 2005-09-21
> I want to add kernel headers but want to make sure I get the right version.

That's an odd output for uname.

It isn't unusual for Synaptic's package name to be diferent than the version number.  It has to be done that way for Synaptic to recognize a package as an 'upgrade' and not as a separate package.  I think the Hoary kernel is up to version 34 or 35 now!  It gets updated for security reasons, etc.

Just download what you think are the right ones.  The first time that you try to compile something it'll probably tell you if it is correct or not.  Every ./configure script that I've used was quick to complain if they didn't match the running kernel.

---

### Post by bob_c_b on 2005-09-22
Thanks, going to try the latest nVidia drivers later so that should be a good test.

---

