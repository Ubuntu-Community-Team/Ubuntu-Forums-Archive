---
title: "Xbox controller"
date: 2006-05-09
forum: Gaming &amp; Leisure
---

### Post by trent dillman on 2006-05-09
...

---

### Post by beniwtv on 2006-05-09
The file at this link is a .patch file for the entrie kernel, I suppose. In that case you won't be able to apply that patch without recompiling, sorry.

But if you have the source of the module (the driver), you could apply the changes manually (If you know about programming...)

Sorry to say this, but these are still counterparts in the linux world ... :-({|=

---

### Post by Monster_user on 2006-05-09
[QUOTE=beniwtv]But if you have the source of the module (the driver), you could apply the changes manually (If you know about programming...)[/QUOTE]
You don't need to know much about programming. You just need to know about the 'diff' and 'patch' options in "make". Which I'm sad to say, that I've forgotten.

You also need the original source code to patch. Which is in the kernel source. Which still requires a partial compile of the kernel. Which also means broken updates when updating the kernel, which is a bad thing when using Dapper.

Unfortunately, it looks like it is too soon to tell if that patch can safely be added to a Kernel, without messing up somebody else's X-Box controller. So I doubt it will be added to Dapper's kernel.

If I new anything about making "*.deb" packages from scratch, I would offer to make you a new Kernel Modules package, with the X-Box controller patch. You would loose it the next time you updated the kernel though.

---

### Post by trent dillman on 2006-05-10
...

---

### Post by trent dillman on 2006-05-10
...

---

### Post by graigsmith on 2006-05-23
i got it working, see that thread here. [http://ubuntuforums.org/showthread.php?t=164040](http://ubuntuforums.org/showthread.php?t=164040)

---

