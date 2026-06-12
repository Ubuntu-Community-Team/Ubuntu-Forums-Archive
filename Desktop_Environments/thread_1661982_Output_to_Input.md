---
title: "Output to Input?"
date: 2011-01-07
forum: Desktop Environments
---

### Post by 71GA on 2011-01-07
Hello!

What does this command mean? Is this some sort of a pipe where output of one program goes to input of another?

```
 bunzip2 < file.tar.bz2 | tar xf -
```

---

### Post by 3Miro on 2011-01-07
I think the idea is to extract a file in two stages. First stage will use bz2 and then it will feed the output into tar.

You should be able to do that with tar alone, if you add the j option:
```
tar -xvjf file.tar.bz2
```

---

### Post by 71GA on 2011-01-07
Ya but i am learning pipng and i dont know why is there an "<" in the beginning of the command i specified and "-" at the end. But your post is useful. I ll keep that in mind ty.

---

### Post by psusi on 2011-01-07
The < redirects the input of bunzip2 from the file.  The | connects the output of bunzip2 to the input of tar.  The - argument to tar tells it to read from its stdin instead of a named file.

---

### Post by 71GA on 2011-01-08
> **psusi said:**
> The < redirects the input of bunzip2 from the file.  The | connects the output of bunzip2 to the input of tar.  The - argument to tar tells it to read from its stdin instead of a named file.
Thank you this was what i have been looking for. 

CHEERS! :popcorn:

---

