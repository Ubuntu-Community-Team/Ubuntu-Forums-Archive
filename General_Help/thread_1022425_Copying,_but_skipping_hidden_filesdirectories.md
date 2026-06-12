---
title: "Copying, but skipping hidden files/directories"
date: 2008-12-26
forum: General Help
---

### Post by josephmo on 2008-12-26
It seems as if the cp utility does not have a switch to exclude hidden files. Am I missing one of the switches? if not, are there any other utilities that would provide this functionality?

---

### Post by taurus on 2008-12-26
I assume this question ties to your other question about moving /home from one partition to another.

[http://www.psychocats.net/ubuntu/separatehome#usingnew](http://www.psychocats.net/ubuntu/separatehome#usingnew)

---

### Post by josephmo on 2008-12-26
> **taurus said:**
> I assume this question ties to your other question about moving /home from one partition to another.

[http://www.psychocats.net/ubuntu/separatehome#usingnew](http://www.psychocats.net/ubuntu/separatehome#usingnew)


No, it has nothing to do with it. 

BTW, the procedure described in the url you included did not work for me. I had to do something else (this was a couple of months ago).

---

### Post by reality1011 on 2008-12-26
why not use the find command with parameters like:

find . -name "*" -exec cp <directory> {} \;

---

### Post by mempman on 2008-12-26
Try this:

ls -a [^.]* | more

---

