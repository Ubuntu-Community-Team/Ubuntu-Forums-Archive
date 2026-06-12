---
title: "How do you remove a soft link"
date: 2009-01-26
forum: General Help
---

### Post by comfixit on 2009-01-26
How do you remove a soft link created with the ln -s command?

---

### Post by jerome1232 on 2009-01-26
```
rm /path/to/symbolic/link
```

It just removes the link, not what the link is pointing at.

For example

```
ln -s test testlink
ls -l
-rw-r--r-- 1 jeremy users 0 2009-01-26 20:25 test
lrwxrwxrwx 1 jeremy users 4 2009-01-26 20:26 testlink -> test
rm testlink
ls -l
-rw-r--r-- 1 jeremy users 0 2009-01-26 20:25 test

```

---

### Post by Iowan on 2009-01-26
**rm** seems to work for me - for a soft link.

I was in current directory - so full path would work better...

---

### Post by cdtech on 2009-01-26
```
unlink <link>
```

---

### Post by snova on 2009-01-27
> **comfixit said:**
> How do you remove a soft link created with the ln -s command?

The same way you would any other file. However you like.

---

