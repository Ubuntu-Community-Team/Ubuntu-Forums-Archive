---
title: "Tarball File"
date: 2009-05-24
forum: General Help
---

### Post by &lt;iostream&gt; on 2009-05-24
H!
I just got back to ubuntu, but there is one thing that I want to find out: Can someone post DETAILED instructions or make a link to a walk through on how to unpack and install tar ball files (.tar.gz or .tar.gz2) Thanks!

---

### Post by PGScooter on 2009-05-24
Hi iostream,

I am a beginner myself. There great instructions and examples on the tar man page (I like it because the examples are even close to the top!)

To read it, type into the terminal: ```
man tar
```

Read that, and if you still are lost, post what you tried and I will try to help.

Welcome back to Ubuntu!!!

---

### Post by mellowd on 2009-05-24
A tar.gz is just a tarred and compressed file. It might contain source code or something else. It'll depend on what's in there in order to know how to install it.

For starters type tar zxvf tarfilename.tar.gz

---

### Post by colau on 2009-05-24
> **<iostream> said:**
> H!
I just got back to ubuntu, but there is one thing that I want to find out: Can someone post DETAILED instructions or make a link to a walk through on how to unpack and install tar ball files (.tar.gz or .tar.gz2) Thanks!
```

tar vxzf filename.tar.gz
./configure
make
make install

```

---

### Post by &lt;iostream&gt; on 2009-05-31
Thanks for the help everyone!

---

