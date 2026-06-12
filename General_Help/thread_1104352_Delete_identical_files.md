---
title: "Delete identical files"
date: 2009-03-23
forum: General Help
---

### Post by NCLI on 2009-03-23
I have ripped a lot of music from various internet radio stations using streamripper, end ended up with a lot of duplicate song. They all have the same name with an added (1), (2), (3), etc.

What I'd like to know is whether there is some kind of command I can use to delete any file with (*).mp3 in its name.

---

### Post by Bachstelze on 2009-03-23
Use a for loop:

```
firas@iori ~ % ls *mp3
bar(2).mp3  bar.mp3  foo(1).mp3  foo(5a).mp3  foo.mp3
firas@iori ~ % for i in *\([0-9]\).mp3; do rm $i; done
firas@iori ~ % ls *mp3
bar.mp3  foo(5a).mp3  foo.mp3

```

Here I deleted only files which have just one digit between the parentheses. If you relly want to delete all the files that have parentheses, regardel of what's between them, do

```
for i in *\(*\).mp3; do rm $i; done
```

---

### Post by ghostdog74 on 2009-03-23
no need for loop 
```

# ls -1
bar(1).mp3
bar(2).mp3
bar(3).mp3
test.txt
# shopt -s extglob
# rm *\(*\).mp3
# ls -1
test.txt


```

---

