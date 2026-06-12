---
title: "suspend not triggered automatically"
date: 2017-05-25
forum: Desktop Environments
---

### Post by 84matte84 on 2017-05-25
Dear all,

I have an HP Elitebook Folio 1040G3 running Ubuntu Mate 16.04 - 4.8.0-52-generic (with disk encryption).
Suspend is working fine when laptop lid is closed but the auto-suspend with timeout is not working neither with AC nor on battery.

Syslog does not report anything related to this.
Please help...
thanks in advance

---

### Post by #&amp;thj^% on 2017-05-26
HP's can be a bit troublesome;
So you will have to use the Terminal to get this Set.
You can use the **"at" **command to schedule any action, including running the commands detailed in that question.
This from "man at"
```
AT(1P)                     POSIX Programmer's Manual                    AT(1P)

PROLOG
       This  manual  page is part of the POSIX Programmer's Manual.  The Linux
       implementation of this interface may differ (consult the  corresponding
       Linux  manual page for details of Linux behavior), or the interface may
       not be implemented on Linux.

NAME
       at — execute commands at a later time

SYNOPSIS
       at [&#8722;m] [&#8722;f file] [&#8722;q queuename] &#8722;t time_arg

       at [&#8722;m] [&#8722;f file] [&#8722;q queuename] timespec...

       at &#8722;r at_job_id...

       at &#8722;l &#8722;q queuename

       at &#8722;l [at_job_id...]


```

So for an example, if you want to hibernate in 30 minutes:

```
echo 'pmi action hibernate' | at now + 30 min
```

Or if you want to suspend at 11:00 pm:

```
echo 'pmi action suspend' | at 11pm
```

And the **"atrm" **command removes jobs created by **"at"**

So if you wanted to remove the suspend command you just made, Reverse with:

```
echo 'pmi action suspend' | atrm 11pm
```
Sorry I like to use the terminal a lot.

---

