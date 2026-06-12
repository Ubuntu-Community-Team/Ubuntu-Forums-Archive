---
title: "dynamic file renaming"
date: 2008-12-08
forum: General Help
---

### Post by dbrooke on 2008-12-08
Hello!

I am looking for some command line help.

I have a bunch of files with certain suffixes:

file1.suffix
file2.suffix
file3.siffix
dir
 file1.suffix
file4.siffix

etc..

I want to be able to traverse the directories and change the suffix names:

something like:
find ./ -name '*.suffix' -type -f -print | mv x.suffix x.newsuffix

Of course, the above does not work. Is this a job for xargs? Any help would be much appreciated.

Donovan

---

### Post by ghantoos on 2008-12-08
I would use *rename*:
```

rename 's/\.suffix$/\.newsuffix/' *
```You can use it with find this way:
```
find . -name '*.suffix' -exec rename 's/\.suffix$/\.newsuffix/'  {} \;
```Hope this helps,
Cheers,

---

### Post by dbrooke on 2008-12-17
Sorry for the late "thanks" reply.. but "thanks!" :-)

---

