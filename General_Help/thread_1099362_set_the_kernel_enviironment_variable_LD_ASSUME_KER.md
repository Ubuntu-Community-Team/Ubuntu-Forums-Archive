---
title: "set the kernel enviironment variable LD_ASSUME_KERNEL"
date: 2009-03-18
forum: General Help
---

### Post by big136 on 2009-03-18
Hi,
I'm installing ORACLE 9i on XUBUNTU and it hangs on :
Link Pending
Copying naeet.o

I found this solution for Linux SLSE :
***************************************
you have to set the kernel enviironment variable LD_ASSUME_KERNEL=2.4.21
******************************

What is the equivalent variable for XUBUNTU ?

How should I do this for XUBUNTU ?

Many thanks.

---

### Post by dusan.saiko on 2009-03-19
Hello, just execute following back command before running oracle installation

export LD_ASSUME_KERNEL=2.4.21

here is some link which describes what this environment variable is for
[http://people.redhat.com/drepper/assumekernel.html](http://people.redhat.com/drepper/assumekernel.html)

---

