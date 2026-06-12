---
title: "Installing a program called &quot;Cluster&quot;"
date: 2011-03-14
forum: Education &amp; Science
---

### Post by lethalfang on 2011-03-14
Anyone has done this before?

I'm trying to install the program called "Cluster" on this website: 
[http://bonsai.hgc.jp/~mdehoon/software/cluster/software.htm](http://bonsai.hgc.jp/~mdehoon/software/cluster/software.htm)

After I installed a bunch of libraries, and ran ./configure, I got this error message: 
```
configure: error: Failed to locate the Motif header files.
Use --without-x if you want to build the command-line version of Cluster 3.0.
Otherwise, use CPPFLAGS to add the Motif header directory to the path.
For example, if Xm.h is in /usr/X11R6/include/Xm, use
./configure CPPFLAGS=-I/usr/X11R6/include

```

So, after locating where Xm is, I did the following:
./configure CPPFLAGS=-I/usr/include

The same message appeared.

I tried this then:
./configure CPPFLAGS=/usr/include

To which I got this error message:
```

/software.htmconfigure: error: C compiler cannot create executables
See `config.log' for more details.

```

Anyone knows what is the issue?

Thanks in advance.

---

### Post by tombart on 2011-04-22
```
aptitude install x11proto-print-dev
```

did the trick for me

Next time check config.log sometimes there might be useful information.

Btw. I'm writing similar clustering software in java, if you would be interested in...

---

### Post by lethalfang on 2011-06-16
Thanks. That worked.

---

