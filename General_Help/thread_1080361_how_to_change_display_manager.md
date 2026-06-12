---
title: "how to change display manager ??"
date: 2009-02-25
forum: General Help
---

### Post by kushal.7 on 2009-02-25
Hi,
I install kde on ubuntu 8.10, & i set the default display manager to kdm, but now i wanted to change it to previous i.e. gdm.
How can i change it ???

---

### Post by fooman on 2009-02-25
open a terminal and try this command:

```
sudo dpkg-reconfigure gdm
```

---

### Post by kushal.7 on 2009-02-25
> **fooman said:**
> open a terminal and try this command:

```
sudo dpkg-reconfigure gdm
```

dpkg-query: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 field name `' must be followed by colon
/usr/sbin/dpkg-reconfigure: gdm is not installed

---

### Post by fooman on 2009-02-25
well if it is not installed,  try installing it:

```
sudo apt-get install gdm
```

---

### Post by kushal.7 on 2009-02-25
> **fooman said:**
> well if it is not installed,  try installing it:

```
sudo apt-get install gdm
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by fooman on 2009-02-25
for that error,  run this:

```
sudo dpkg --configure -a
```then:  

```
 sudo apt-get update
```

then finally:

```
 sudo apt-get install gdm
```

hope that works for you.

---

### Post by kushal.7 on 2009-02-25
> **fooman said:**
> for that error,  run this:

```
sudo dpkg --configure -a
```then:  

```
 sudo apt-get update
```

then finally:

```
 sudo apt-get install gdm
```

hope that works for you.


```
sudo dpkg --configure -a
```
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 field name `' must be followed by colon.

---

### Post by letmekilluplz on 2009-05-13
I'm having the same problem changing from kdm back to gdm Ill try this post when I get home

---

