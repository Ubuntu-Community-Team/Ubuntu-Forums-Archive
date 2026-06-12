---
title: "replacing &quot;=&quot; to space"
date: 2009-04-07
forum: General Help
---

### Post by vandinsh on 2009-04-07
Hello,

Is there any command how to replace all "=" to a whitespace in a text file?

Thanks!! :)

---

### Post by kellemes on 2009-04-07
> **vandinsh said:**
> Hello,

Is there any command how to replace all "=" to a whitespace in a text file?

Thanks!! :)

From terminal..
```
sed -i 's/=/ /g' <filename>
```

For more info about "sed" type..
```
man sed
```
Or visit.. [http://www.manpagez.com/man/1/sed/]("http://www.manpagez.com/man/1/sed/")

---

### Post by aeiah on 2009-04-07
if its just for one text file, you can just use almost any gui text editor's 'find and replace' feature

---

