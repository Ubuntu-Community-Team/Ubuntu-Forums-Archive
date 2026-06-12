---
title: "Search and replace in content"
date: 2005-05-14
forum: Desktop Environments
---

### Post by matid on 2005-05-14
Does anyone know how to replace a string with another in all files in directory?
I know how to search in the content (grep *string* * -R), but is there a way to share found string to #string? I'd by also satisfied by deleting the line with found string.

---

### Post by GrumpySmurf on 2005-05-14
You'll probably be interested in the 'sed' command in a for loop.  Very simple example (bash):

```
$ for file in *
do
    sed 's/string/newstring/g' $file > ${file}.1
    mv ${file}.1 $file
done
```

---

