---
title: "Maxima: read() doesn't pause for input"
date: 2007-06-15
forum: Education &amp; Science
---

### Post by silbar on 2007-06-15
It just gives back "false":

(%i1) read("enter x:");
enter x: 
(%o1) false

Am I not understanding how this should work?

   Dick Silbar

---

### Post by WW on 2007-06-15
I just tried it, and I got the same thing. The read function doesn't appear to actually read anything.  The arguments to the function are printed, but then it just goes to another command input prompt.  I am running Dapper, which has version 5.9.2 of maxima.
```

~$ maxima
Maxima restarted.
(%i1) x: read("Enter x: ")$
Enter x:
(%i2)

```

I downloaded the source for version 5.12.0 from the Maxima web page, and did a "Lisp only" installation, and the read command worked as described in the documentation.
```

~/install/maxima/maxima-5.12.0/src$ sh maxima
Maxima 5.12.0 http://maxima.sourceforge.net
Using Lisp CLISP 2.38 (2006-01-24)
Distributed under the GNU Public License. See the file COPYING.
Dedicated to the memory of William Schelter.
This is a development version of Maxima. The function bug_report()
provides bug reporting information.
(%i1) x: read("Enter x: ")$
Enter x:
42;
(%i2) x;
(%o2)                                 42
(%i3)

```

---

