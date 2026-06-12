---
title: "vim search and replace"
date: 2009-05-21
forum: General Help
---

### Post by salakhate on 2009-05-21
Hi all,
I am using vi in Ubuntu. I just want to search something like: '../../linux' and replace it with '/home/linux'.
Simple search and replace says "trailing characters"
can anyone help me with this.

Thanks in advance!

---

### Post by _Purple_ on 2009-05-21
```
:%s/..\/..\/linux/\/home\/linux/g
```

---

### Post by salakhate on 2009-05-21
Hi _Purple_,
Thanks a lot!
:D

---

### Post by colau on 2009-05-21
That's tricky.

---

### Post by _Purple_ on 2009-05-21
> **salakhate said:**
> Hi _Purple_,
Thanks a lot!
:D

You are welcome :)

---

### Post by ad_267 on 2009-05-21
Just a note of caution and for future reference, those periods will match any character, so "..\/..\/linux" will match "ab/yz/linux", "12/89/linux" etc. To make sure you're only matching an actual period you should escape the . with a backslash, ie. "\.". Although it probably doesn't matter in this case because you're unlikely to have anything else that will match.

---

### Post by salakhate on 2009-05-21
Thanks!
could you let me know how the code above would look like with the "\." that avoids matching all characters?

---

### Post by ad_267 on 2009-05-21
It would be quite messy really, you just need a backslash in front of all the "."s and all the "/"s:

```
:%s/\.\.\/\.\.\/linux/\/home\/linux/g
```

To tidy things up, you don't have to use a forward slash to separate the search and replace terms, you can use any character you want. That way you don't have to escape the forward slashes. Eg for a $ sign:

```
:%s$\.\./\.\./linux$/home/linux$g
```

---

### Post by salakhate on 2009-05-22
Hi ad_267!
Thanks! it helped me a lot.

---

