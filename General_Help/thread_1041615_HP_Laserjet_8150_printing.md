---
title: "HP Laserjet 8150 printing"
date: 2009-01-16
forum: General Help
---

### Post by ubrox on 2009-01-16
First, Where is the "Printing" category?

OK, I am printing to a HP LaserJet 8150. When I print anything, some characters are printed as small squares, as if a font is missing. 

Ubuntu detected and installed this network printer automatically. I did not make any changes. 

How do I avoid those? 

Thanks,

---

### Post by rbmorse on 2009-01-16
Does this bug report against HPLIP look like the same thing you're seeing?

[https://bugs.launchpad.net/hplip/+bug/291318](https://bugs.launchpad.net/hplip/+bug/291318)

also

[https://bugs.launchpad.net/ubuntu/+source/foomatic-db/+bug/277404](https://bugs.launchpad.net/ubuntu/+source/foomatic-db/+bug/277404)

---

### Post by ubrox on 2009-01-17
yeah! thanks. marking as solved here

---

### Post by ubrox on 2009-01-17
How to mark this as solved? There is no such option in "Thread Tools"

---

### Post by gallen53 on 2009-02-15
As far as I can tell this is NOT solved.  There's a bug in the HP driver for PostScript-3.  I'm going to post more information on the thread:

[https://bugs.launchpad.net/hplip/+bug/291318](https://bugs.launchpad.net/hplip/+bug/291318)

One work around is to reconfigure Ubuntu to think it's driving a LaserJet-III.  This is a poor solution because most of the HP-8150 functionality is lost when you do this.

---

