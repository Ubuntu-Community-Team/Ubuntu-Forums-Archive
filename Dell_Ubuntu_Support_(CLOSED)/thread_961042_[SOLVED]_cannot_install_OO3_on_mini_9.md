---
title: "[SOLVED] cannot install OO3 on mini 9"
date: 2008-10-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ARhere on 2008-10-27
not sure why but I cannot seem to install Open Office 3 on the Dell mini 9.  When i try to install the *.deb, this is what i get.
```
$ sudo dpkg -i *.deb
dpkg: error processing ooobasis3.0-base_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-binfilter_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-calc_3.0.0-9_i386.deb (--install):
 package archite$ sudo dpkg -i *.deb
dpkg: error processing ooobasis3.0-base_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-binfilter_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-calc_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-core01_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
 cture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-core01_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)...
```

I know it says the architecture is wrong but I was positive the Intel Atom is x86 compatable... am I wrong?!?!

-AR

---

### Post by 2damncommon on 2008-10-27
There is a "-force-architecture" option for dpkg. I am not about to tell you you should use it. But you can.

Maybe google "open office lpia" and see if there is a reason not to do that?"

---

### Post by ARhere on 2008-10-28
I did before posting,but an answer is not clear.  All I see is that the force option "should" work.  But I wanted to double-check the ubuntu forums to see if anyone else has tried this.

-AR

---

### Post by yakker.yak on 2008-10-28
> **ARhere said:**
> not sure why but I cannot seem to install Open Office 3 on the Dell mini 9.  When i try to install the *.deb, this is what i get.
```
$ sudo dpkg -i *.deb
dpkg: error processing ooobasis3.0-base_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-binfilter_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-calc_3.0.0-9_i386.deb (--install):
 package archite$ sudo dpkg -i *.deb
dpkg: error processing ooobasis3.0-base_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-binfilter_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-calc_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-core01_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)
 cture (i386) does not match system (lpia)
dpkg: error processing ooobasis3.0-core01_3.0.0-9_i386.deb (--install):
 package architecture (i386) does not match system (lpia)...
```

I know it says the architecture is wrong but I was positive the Intel Atom is x86 compatable... am I wrong?!?!

-AR

Please see the post by feranick on getting skype to work here (should be a similar process for OpenOffice and other DEBs outside of the standard repositories):
[http://ubuntuforums.org/showthread.php?t=910487&page=55]("http://ubuntuforums.org/showthread.php?t=910487&page=55").

---

