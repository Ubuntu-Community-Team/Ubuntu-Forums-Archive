---
title: "Installing Netscape"
date: 2009-02-04
forum: General Help
---

### Post by nemiux on 2009-02-04
I need to know how to install netscape on my computer (or anything for tar.gz at that matter)
I downloaded it for linux:
[http://browser.netscape.com/](http://browser.netscape.com/)
Next what i have to do?



Thanks

---

### Post by Fixman on 2009-02-04
> **nemiux said:**
> I need to know how to install netscape on my computer (or anything for tar.gz at that matter)
I downloaded it for linux:
[http://browser.netscape.com/](http://browser.netscape.com/)
Next what i have to do?



Thanks

Generally, inside the .tar.gz theres a file called "INSTALL" or "README" that tells you how to install the program. But in the most part, it is

```

cd directory_of_file
./configure
make
sudo make install

```

---

### Post by nemiux on 2009-02-04
It gives me this message:
nemiux@ubuntu:~/Desktop/Netscape$ sudo make install
[sudo] password for nemiux: 
make: *** No rule to make target `install'.  Stop.
In readme it only gives me link to main page, i can't find anything there

---

### Post by nemiux on 2009-02-05
So, could anyone help me with that?

---

