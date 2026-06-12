---
title: "man command not working"
date: 2006-10-06
forum: Desktop Environments
---

### Post by ggeldenhuys on 2006-10-06
When I try and use the *man* command, I keep getting these errors scrolling over the screen.  I cannot use man at all.  Any ideas what I can do. 

So far I have reinstalled the **man-db** and **coreutils** packages which contain the *man* and *basename* programs. That made no difference.

----------------
[graemeg-linux] cron.weekly > man crontab
basename: invalid option -- a
Try `basename --help' for more information.
basename: invalid option -- a
Try `basename --help' for more information.
basename: invalid option -- a
Try `basename --help' for more information.
basename: invalid option -- a
Try `basename --help' for more information.
basename: invalid option -- a
Try `basename --help' for more information.
----------------

I am using Ubuntu 6.06 on x86 platform. My other computer uses Ubuntu 5.10 and there the man command works fine.

Regards,
  - Graeme -

---

### Post by Arndt on 2006-10-06
> **ggeldenhuys said:**
> When I try and use the *man* command, I keep getting these errors scrolling over the screen.  I cannot use man at all.  Any ideas what I can do. 

So far I have reinstalled the **man-db** and **coreutils** packages which contain the *man* and *basename* programs. That made no difference.

----------------
[graemeg-linux] cron.weekly > man crontab
basename: invalid option -- a
Try `basename --help' for more information.
basename: invalid option -- a
Try `basename --help' for more information.
basename: invalid option -- a
Try `basename --help' for more information.
basename: invalid option -- a
Try `basename --help' for more information.
basename: invalid option -- a
Try `basename --help' for more information.
----------------

I am using Ubuntu 6.06 on x86 platform. My other computer uses Ubuntu 5.10 and there the man command works fine.

Regards,
  - Graeme -

The first thing I would do is
```
which man
```

I suspect that your 'man' is something other than you expect.

---

### Post by ggeldenhuys on 2006-10-06
> **Arndt said:**
> The first thing I would do is
```
which man
```

I suspect that your 'man' is something other than you expect.


Just did, and I think you are on to something... 

------------------------
[graemeg-linux] cron.weekly > which man
man is a function
man ()
{
    xtitle The $(basename $1|tr -d .[:digit:]) manual;
    man -a "$*"
}
man is /usr/bin/man
man is /usr/bin/X11/man

[graemeg-linux] cron.weekly > ls -l /usr/bin/man
lrwxrwxrwx 1 root root 17 2006-08-05 16:14 /usr/bin/man -> ../lib/man-db/man*
------------------------

The "man is a function" didn't seem right.  I then remember I copied a whole bunch of example bash enhancement (functions, aliases, etc) into my .bashrc file.  Searched the .bashrc, and found the offending function called *man*.  ](*,)    
Deleted it, and *man* works 100% again. 

Thanks for pointing me in the right direction!

Regards,
  - Graeme -

---

