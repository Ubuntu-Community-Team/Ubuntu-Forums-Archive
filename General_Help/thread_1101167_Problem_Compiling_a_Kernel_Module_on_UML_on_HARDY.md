---
title: "Problem Compiling a Kernel Module on UML on HARDY"
date: 2009-03-20
forum: General Help
---

### Post by amitarora.iitb on 2009-03-20
Hello all, I am a bit new to UML(User Mode Linux) and stuff. I installed UML on my hardy machine.
I am trying to compile a kernel module on the UML. 

The kernel module does not compile with a lot of errors. 
uname -r gives 2.6.22-rc5 the exact headers of which i could not find so I have installed 2.6.22-generic headers.

The makefile is as under 
```

obj-m += nfq-test-1.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) ARCH=um modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

since uname -r and the headers installed have diff dir I made a symlink in the /usr/src and /lib/modules so that the output of uname -r points to the correct directory 

On compiling it gives a lot of errors 

Can somebody please help me out.

Thanks in Advance

---

### Post by MaindotC on 2009-03-20
UML stands for Unified Modeling Language and it has nothing to do with the linux kernel.  It's a way of displaying conceptual things, mostly database relationships, cardinality, and strong/weak relationships.

---

### Post by amitarora.iitb on 2009-03-20
It also stands for User Mode Linux which is an open Source Virtual Machine for linux. 

[http://user-mode-linux.sourceforge.net/](http://user-mode-linux.sourceforge.net/)

---

