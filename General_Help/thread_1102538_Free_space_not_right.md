---
title: "Free space not right"
date: 2009-03-21
forum: General Help
---

### Post by sv1cdn on 2009-03-21
Hello!
Using 8.10 Ubuntu, Disk analyzer reports used 31.7GB but when it finishes scanning it shows only 20.9GB space!
Any idea or some bug?
How can I run CLI command to get actual space used?
Take care!

---

### Post by taurus on 2009-03-21
Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by dcstar on 2009-03-21
> **sv1cdn said:**
> Hello!
Using 8.10 Ubuntu, Disk analyzer reports used 31.7GB but when it finishes scanning it shows only 20.9GB space!
Any idea or some bug?
How can I run CLI command to get actual space used?
Take care!

AFAIK Disk Analyzer runs with user privileges only and will not count files that have root only access.

If you want it to see **everything**, create a launcher with the following:

```
gksudo baobab
```

---

### Post by sv1cdn on 2009-03-22
Found it! Thanks all!
I did run baobab with sudo in a terminal and just got 2 more gigabytes. But I was actually missing 13+GB.
Found command du (display usage). Run it as sudo du -m from root and realized that in /var directory there were many backup files made by sbackup software. These files were not readable by baobab at all!
Take care.

---

