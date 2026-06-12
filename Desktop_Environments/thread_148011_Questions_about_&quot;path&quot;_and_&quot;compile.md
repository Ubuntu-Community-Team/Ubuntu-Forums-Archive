---
title: "Questions about &quot;path&quot; and &quot;compile&quot;"
date: 2006-03-21
forum: Desktop Environments
---

### Post by Lin-X on 2006-03-21
I have been trying to install something (anything!) from source, This is part of an effort to teach myself, a non-programming newb, about Linux; I made a list of things I think I should be able to do and I am working my way through the list: install from source, back up my Linux partition, configure my hardware, recompile the kernal, and so on.
   While trying to install a small journal program, I came to the compile and got an error message saying, "There is no C comiler in your path." I think I understand the message but I don't know how to correct the problem.

   Another problem: trying to compile another small ap, I was surprised to be told,
when I typed ./compile that "there is no such command or file name. I know it's in there because I used it before (see above) and didn't get this error message. So what's up with that?

   All answers welcome and appreciated.

---

### Post by jrib on 2006-03-21
to build stuff, you need the build-essential package:

```
sudo aptitude install build-essential
```

And you are probably referring to ./configure, not ./compile.

See [https://wiki.ubuntu.com/CompilingSoftware](https://wiki.ubuntu.com/CompilingSoftware) for a nice guide.  Be sure to use ``checkinstall'', instead of make ``install''.

---

### Post by Lin-X on 2006-03-21
Thanks for the reply, Jason, and you are right, I did mean "configure" and that really is what I typed, ./configure. Sorry for the rediculous error. Your answer helped anyway. thanks again. I'll start over.:cry:

---

