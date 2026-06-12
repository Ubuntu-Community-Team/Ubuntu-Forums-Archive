---
title: "Installing RP-PPPoE on ubuntu"
date: 2005-02-06
forum: Desktop Environments
---

### Post by Syrex on 2005-02-06
Hello all  8) 
First of all I'm hoping that is the right forum for this question.
I have pppoe connection.. 
How I can install RP-PPPoE? ([http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php](http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php)), when I'm trying to install it I'm getting an error that I don't have gcc...

Thanking you in advance.

---

### Post by Canguçu on 2005-02-06
Ubuntu doesn't include GCC by default (because it causes security concerns), so you can't just download a tarball from the web and compile it. Unfortunatelly, the ubuntu apt repositories do not have rp-pppoe, so you have two options:

1) Install gcc with Synaptic (computer menu -> system configuration -> synaptic)
NOT recommended, but works.

2) Use ppoeconf, included by default in Ubuntu installations.

I hope I could help you.

---

### Post by Syrex on 2005-02-06
ohhhh . I didn't knew that ppoeconf included in Ubuntu...

10q Canguçu

---

