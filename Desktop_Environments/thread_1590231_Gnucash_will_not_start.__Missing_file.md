---
title: "Gnucash will not start.  Missing file"
date: 2010-10-07
forum: Desktop Environments
---

### Post by JimGvo on 2010-10-07
I get the following:

ERROR: No such file or directory: "/usr/share/guile/1.6/slib/init/slib/require.scm"

The file does not exist.  I have removed gnucash and guile-1.6 entirely along with a bunch of other stuff that depended on guile.  Then I reinstalled gnucash.  Didn't help.

I'm running Ubuntu 10.04.  

It used to work.  I don't know what has changed.

Thanks,
Jim.

---

### Post by RHTopics on 2010-10-07
I am running Ubuntu 10.04 with Gnucash installed.

Gnucash starts up for me.  You are right about file "/usr/share/guile/1.6/slib/init/slib/require.scm", it does not exist.

Found this older message posting concerning Gnucash that may apply to your situation:

[http://ubuntuforums.org/showthread.php?t=445495](http://ubuntuforums.org/showthread.php?t=445495)

I guess the take away from it for you, try removing or reinstalling guile-1.8, and see if that fixes the problem.

---

### Post by JimGvo on 2010-10-08
> **RHTopics said:**
> I am running Ubuntu 10.04 with Gnucash installed.

Gnucash starts up for me.  You are right about file "/usr/share/guile/1.6/slib/init/slib/require.scm", it does not exist.

Found this older message posting concerning Gnucash that may apply to your situation:

[http://ubuntuforums.org/showthread.php?t=445495](http://ubuntuforums.org/showthread.php?t=445495)

I guess the take away from it for you, try removing or reinstalling guile-1.8, and see if that fixes the problem.

Thanks, it was already gone:
> rc  guile-1.8                                  1.8.7+1-3ubuntu1                                           The GNU extension language and Scheme interpreter
rc  guile-1.8-libs                             1.8.7+1-3ubuntu1                                           Main Guile libraries

But installing it didn't help

```

 gnucash
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

ERROR: In procedure open-file:
ERROR: No such file or directory: "/usr/share/guile/1.6/slib/init/slib/require.scm"

```

Jim.

---

### Post by Turtle.net on 2011-03-02
It seems that the problem is solved by installing guile-1.6-dev.
For a problem of deopendencies, apt suggested to remove libreadline5-dev. THat's what I have done, and now Gnucash is working again :)

---

