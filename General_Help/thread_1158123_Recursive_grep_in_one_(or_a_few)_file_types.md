---
title: "Recursive grep in one (or a few) file types"
date: 2009-05-13
forum: General Help
---

### Post by joelholdsworth on 2009-05-13
Hi,

Is there an easy way to recursively search for a string within the files in a directory tree, but only looking in one (or a few) file types. So for example I might want to search for all the instances of a string within a source tree, but only looking *.php files, but not everything else - *.jpg etc.?

Is there an easy command line, or an easy GUI way to do this?

Thanks
Joel

---

### Post by kanikilu on 2009-05-13
You can certainly do it from the command line, but an easy but powerful GUI tool that I like to use for things like this is called **regexxer**, the package is in universe.

---

### Post by Grenage on 2009-05-13
I would personally make use of ls to find the files you are after, then pipe that into grep.  I'm not at my linux machine at the moment, but if nobody else posts an example before I get home, I'll write one for you.

---

### Post by lswb on 2009-05-13
Check out the --include option for grep in the grep man page, I believe it would be something like this:

grep -R --include="*.php" "some string" DirectoryName

Another way is to use  the "find" command with the exec option, something like:

find directoryname -name "*.php" -exec grep "some string" '{}' \;

My syntax may need a little fine tuning but either approach should work.

---

### Post by Alekz_ on 2009-05-13
Well.. You can run `ls` with `grep`:

```
ls -lR |grep ".ext"
```

It should work...

---

