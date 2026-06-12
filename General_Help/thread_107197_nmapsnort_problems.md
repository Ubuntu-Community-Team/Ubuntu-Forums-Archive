---
title: "nmap/snort problems"
date: 2005-12-22
forum: General Help
---

### Post by almostlinux on 2005-12-22
i tried to compile nmap 3.95 .. it said it had a problem with the libpcre..so i removed libpcre from the package manager .. and i got libpcre source (pcre-6.4) and compiled it.
after that the nmap compilation/installation went on smoothly, but when i try to run it, it says

```

nmap: error while loading shared libraries: libpcre.so.0: cannot open shared object file: No such file or directory

```

i had nmap3.93 before(with which i didn't have any problems), and i installed 3.95 over it

the same thing happens with snort-2.4.3 

the synaptic packages (for nmap and snort) are not updated and also i want to compile everything myself

any help? thanks in advance :)

---

### Post by almostlinux on 2005-12-23
bump...

---

### Post by Myst3K on 2006-01-01
Try this:

```
cp /usr/local/lib/libpcre.so.0 /usr/lib
```

---

### Post by almostlinux on 2006-01-03
That fixed it. Thanks !! :D :D

---

