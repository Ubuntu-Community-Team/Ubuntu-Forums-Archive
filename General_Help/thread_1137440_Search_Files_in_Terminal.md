---
title: "Search Files in Terminal"
date: 2009-04-25
forum: General Help
---

### Post by Ansraliant on 2009-04-25
Hi, i need to do the following:
by using one command line in the terminal i need to get a list of all the files with read, write and excecute permissions for all users.
I believe i have to use something like "ls -l" with pipe | and grep somehow, i just do not how.

Thanks in advance.

---

### Post by conscious on 2009-04-26
```
man find
```
See "-perm" test.

---

### Post by andrew.46 on 2009-04-27
Hi Ansraliant,

> **Ansraliant said:**
> Hi, i need to do the following:
by using one command line in the terminal i need to get a list of all the files with read, write and excecute permissions for all users.
I believe i have to use something like "ls -l" with pipe | and grep somehow, i just do not how.

As conscious has suggested you might be best to use 'find'. If you are interested in a 'gentle' introduction to 'find' I have written such a guide:

Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

I guess if you were after such a list for your home directory only, as an example, you could use something like:

```
find $HOME -perm 777
```

I imagine that this is what your question implies?

Andrew

---

