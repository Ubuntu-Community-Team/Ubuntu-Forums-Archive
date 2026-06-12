---
title: "wordlist: check for duplicate words"
date: 2009-04-05
forum: General Help
---

### Post by sudo_chop on 2009-04-05
Does anyone know of an existing tool or a script I could write that will check a huge wordlist I have compiled for duplicate lines?

---

### Post by Meson on 2009-04-05
You could build a binary search tree that sorts in lexicographical order.  If you have any collisions as you build the tree, you've found a duplicate.

---

### Post by koenn on 2009-04-05
```
uniq
man uniq
```

What y're up to ? preparing a dictionary attack ?

---

### Post by lovinglinux on 2009-04-05
```
cat file.txt | sort -u > sortedfile.txt
```

---

### Post by sudo_chop on 2009-04-05
Hey thanks for the suggestions guys. It seems like sort -u and uniq do about the same thing, right? I used sort -u on a small file to test it out and it worked perfectly.

> **koenn said:**
> What y're up to ? preparing a dictionary attack ?

Dont worry, its legit. ;)

Thanks again

---

### Post by lovinglinux on 2009-04-05
> **sudo_chop said:**
> Hey thanks for the suggestions guys. It seems like sort -u and uniq do about the same thing, right? I used sort -u on a small file to test it out and it worked perfectly.

I never used *uniq*, but *sort -u* will sort the lines and remove duplicates.

---

### Post by bodhi.zazen on 2009-04-06
Moved to general help.

---

