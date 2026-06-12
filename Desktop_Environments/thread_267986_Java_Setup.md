---
title: "Java Setup"
date: 2006-09-29
forum: Desktop Environments
---

### Post by gtmtnbiker98 on 2006-09-29
Recently migrated from SuSE and am curious as to the easiest way to install Flash and Java support for 6.06?

---

### Post by T_W on 2006-09-29
Both are listed in "Add/Remove Applications" applet off of the Applications menu.

If you install Sun JDK 1.5, then you also can run update-java-alternatives to point your system at the Sun JDK instead of gij/gcj.

---

### Post by dannyboy79 on 2006-09-29
i actually used automatix for this but to each his own.

---

### Post by gtmtnbiker98 on 2006-09-29
Found Flash; however, when searching Synaptic and apt-get I cannot for the life of me find Java via JRE or SUN lookkups.  What am I missing to get Java installed?  Acrobat would be nice too; however, a little off topic.  

I would like to stay with the Deb's as compared to mucking up the system compiling from source.

---

### Post by T_W on 2006-09-29
Its all in there.

You may need to enable additional repositories to get non-free or commercial applications visible in apt-get/synaptic.

The "Add/Remove Programs" applet will enable the necessary repositories automatically (which is a why its a nice place to start).

I beleive the Sun JRE 1.5 package is named sun-java5-bin and its in the Multiverse repository.

From the "Add/Remove Programs" applet its called "Sun Java 5.0 Runtime".  You probably need to click on the "Show unsupported applications" and "Show commercial applications" checkboxes to see it.

Acrobat is also in their.  Its called "Adobe Reader".  Evnince does a pretty good job on PDFs though.

---

### Post by gtmtnbiker98 on 2006-09-29
I didn't have show commercial software checked.  I'm too used to Yast, I guess.  New package manager, a little learning curve.  I'll catch on in a few.  Thanks.

---

### Post by gtmtnbiker98 on 2006-09-29
Oops, still trouble.  When I try to add Sun-Java5-BIN and/or Adobe Reader, I receive the following error:

"Not available in any software channel;" however, all the repositories are enabled (I think).  Ideas?

---

### Post by T_W on 2006-09-29
Is this in Synaptic, apt-get, or "Add/Remove Programs"?

In my experience, "Add/Remove Programs" would prompt me to enable the extra repositories and then would enable them automatically if needed.

In case it doesn't, I think this is all that involved is the following

Go to **/etc/apt/sources.list.d** directory and create two files named :

**dapper-multiverse.list** with contents

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper multiverse
deb http://security.ubuntu.com/ubuntu dapper-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates multiverse

```

and **dapper-universe.list** with contents:

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates universe
```

---

