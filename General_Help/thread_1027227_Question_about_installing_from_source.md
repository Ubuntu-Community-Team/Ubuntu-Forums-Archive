---
title: "Question about installing from source"
date: 2009-01-01
forum: General Help
---

### Post by johnnyxxxcakes on 2009-01-01
I downloaded the TinyFugue source, and I did the usual ./configure, then make, and then sudo make install. When I install it, does it install it to the location from which was extracted from the original archive, or somewhere else on my computer as well?

---

### Post by adult swim on 2009-01-01
check in /usr/local/bin

---

### Post by johnnyxxxcakes on 2009-01-01
> **adult swim said:**
> check in /usr/local/bin

It seemed to have added the folders "bin" and "share" to /home/john. I don't know if I like those there.

---

### Post by Tim Sharitt on 2009-01-01
Your home directory may be the de fault prefix. To get it to install in a certain directory, you need to set the --prefix option in configure. 
For example to install in /usr (/Usr/bin, /usr/lib, or whatever):
```
./configure --prefix=/usr
```

---

### Post by johnnyxxxcakes on 2009-01-01
> **Tim Sharitt said:**
> Your home directory may be the de fault prefix. To get it to install in a certain directory, you need to set the --prefix option in configure. 
For example to install in /usr (/Usr/bin, /usr/lib, or whatever):
```
./configure --prefix=/usr
```

Thank you. I believe this has addressed my question.

---

### Post by johnnyxxxcakes on 2009-01-01
Would it be safe for me to delete the "bin" and "share" folders that were created in my home directory if I wanted to remove TinyFugue?

---

### Post by Tim Sharitt on 2009-01-01
yes, if that's the only place it was installed and nothing else was installed there, deleting the folders should remove it like it was never there.

---

