---
title: "Subspace installation error..."
date: 2005-09-17
forum: Gaming &amp; Leisure
---

### Post by YourSurrogateGod on 2005-09-17
Ok, I'm trying to install subspace for a friend and I'm having a problem when I'm going through the steps in order to make it go. I tried to run the executable, but I'm getting the below error message, anyone know why?
```
$ ./space
./space: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

```

---

### Post by helpee on 2006-05-07
have the same exact problem, I think I know why, but I don't know how to fix it.

In the README it says that doing the "./space" will create a new directory called ".SnS" and put a bunch of files into it. In my experience with Ubuntu, directory names with punctuations besides hyphens and underscores just don't work in most apps. Punctuation usually is an operator in linux, and will just mess things up with directories unless you want to do something specific and know what you are doing.

The way to fix it is probably to change the new target directory name in the source, but that is where my abilities with linux come to a screeching halt, sorry!
There is a SnS.bin one directory down in the "data" directory, but I don't know how to edit it or if it's even important.

Some help with this would be greatly appreciated, I miss playing this game terribly!

---

