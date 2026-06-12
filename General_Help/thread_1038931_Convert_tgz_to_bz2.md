---
title: "Convert tgz to bz2"
date: 2009-01-14
forum: General Help
---

### Post by rigged 00 on 2009-01-14
Hi

I was hopping someone can help (as I am not the best with Linux/ubuntu). I am trying to convert a few .tgz and .tbz archives we have to .bz2 format.

I found the below thread on how to convert bz2 to tgz but I am not sure how to do it for the other way around (tgz to bz2).

[http://ubuntuforums.org/showthread.php?t=646152](http://ubuntuforums.org/showthread.php?t=646152)

---

### Post by heindsight on 2009-01-14
well, firstly tbz is a shorthand for tar.bz2 just as tgz is for tar.gz so you won't have to do anything for the .tbz files (if you want you can rename them).

To convert file.tgz to file.tar.bz2, do:
```
gunzip -c file.tgz | bzip2 > file.tar.bz2
```

---

### Post by rigged 00 on 2009-01-14
Thanx for the info

How would I be able to use the code to convert a whole bunch of files?

```
gunzip -c file.tgz | bzip2 > file.tar.bz2
```

only does a single file to another single file and using a wild card *, doesn't work...

Any suggestions for doing this with multiple files?

---

### Post by iponeverything on 2009-01-14
from inside of a directory:

```

ls | awk -F tgz '{print "gunzip -c "$1"tgz | bzip2 > "$1"tar.bz2}' |sh 

```

---

### Post by heindsight on 2009-01-14
If you want to do it for all .tgz files in the current directory, you can do:
```

ls *.tgz | while read f; do
    n=${f%.tgz};
    gunzip -c "$f" | bzip2 > "$n.tar.bz2";
done

```

If you want to also delete the .tgz file after doing the conversion you could add:
```
rm "$f";
``` to the code above. (put it after the gunzip.. line and before the done line.

---

### Post by rigged 00 on 2009-01-14
Great that worked Thanks. It created a bz2 file for each of the tgz files.

---

