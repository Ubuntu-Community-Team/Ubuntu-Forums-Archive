---
title: "Script question"
date: 2009-01-17
forum: General Help
---

### Post by BradC78 on 2009-01-17
A general Linux script question...  I am trying to write a script that will show the following for the files in current working directory:

<FileName> <LineCount> <WordCount>

I have the following, but it doesn't put everything on one line.  Anyone know how to accomplish this?  Thanks!!!

```
for filename in `ls`
do
  echo $filename
  cat $filename | wc -lw
done
```

---

### Post by Bachstelze on 2009-01-17
```
for filename in `ls`
do
  echo -n $filename
  cat $filename | wc -lw
done
```

([font="monospace"]echo -n[/font] will not append a newline character at the end of the input string.)

---

### Post by BradC78 on 2009-01-17
THANKS!  Works great!

---

