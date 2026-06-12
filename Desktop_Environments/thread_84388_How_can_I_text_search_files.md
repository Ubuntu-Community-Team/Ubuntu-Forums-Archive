---
title: "How can I text search files?"
date: 2005-10-30
forum: Desktop Environments
---

### Post by Sunnz on 2005-10-30
Well, I want to search for files that containt the string "foobar", how can I do it?

I tried this but no luck:
grep -i "foobar" /*

Help please! Thank you!

---

### Post by dbott67 on 2005-10-31
You could install [Beagle]("http://www.gnome.org/projects/beagle/") from Synaptic.

-Dave

---

### Post by ltmon on 2005-10-31
To search recursively (i.e. in all subdirectories) from the current directroy for a string

> grep -R searchterm *

should be fine.

> man grep

gives you all the strange options you can specify (including -i for ignore case).

L

---

### Post by 23meg on 2005-10-31
I often use ```
cat *.txt |grep -i "STRING" 
``` to locate something in a bunch of text files, but this won't return filenames, just the matching strings themselves. 

```
grep -i "STRING" -H *.txt
``` should return what you want though.

---

### Post by frodon on 2005-10-31
The problem i often have with grep is that it not go in sub-directories even with -r option. So i use this command to search a text in files (with .txt extension here) including all sub-directories : ```
grep -i "STRING" `find . -name "*.txt" -print`
```

---

### Post by bnutting on 2005-10-31
I just simply do 'grep -irl STRING *
This will give you the file names in all directories/subdirectories that contain STRING ignoring case.

---

