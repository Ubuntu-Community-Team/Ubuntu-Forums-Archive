---
title: "Multiple versions of tclsh"
date: 2008-06-06
forum: Desktop Environments
---

### Post by quantum5 on 2008-06-06
I am interested in having two separate commands for both tcl8.4 and tcl8.5.  I know they are in separate packages already and I know it is possible to set it up for multiple versions, see: [http://tmml.sourceforge.net/doc/tcl/tclsh.html]("http://tmml.sourceforge.net/doc/tcl/tclsh.html")

So, how do I go about doing that in Ubuntu?

---

### Post by quelx on 2008-06-07
You can install both.  You'll get two binaries **tclsh8.4** and **tclsh8.5** just use the full name to pick which one gets used.  The common one **tclsh** will just be a *symlink* to one of the two versions.

```
sudo apt-get install tcl8.4 tcl8.5
```

---

