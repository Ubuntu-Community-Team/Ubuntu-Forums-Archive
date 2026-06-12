---
title: "[CUPS] - Unable to print : is esp ghostscrip installed"
date: 2005-06-10
forum: Desktop Environments
---

### Post by Pierre A on 2005-06-10
Hi all,

On a freshly installed hoary, I am not able to print.
The printer worked perfectly on ohter linux distros (another hoary and mdk)

The message in the /var/log/cups/error.log is :
```
New printer 'FS-1000+' added by 'root'.
 Adding start banner page "none" to job 1.
 Adding end banner page "none" to job 1.
 Job 1 queued on 'FS-1000+' by 'me'.
 Unable to convert file 0 to printable format for job 1!
 Hint: Do you have ESP Ghostscript installed?
 Hint: Try setting the LogLevel to "debug".
``` 

I tried : 
```
 gs -v
ESP Ghostscript 7.07.1 (2003-07-12)
Copyright 2003 artofcode LLC and Easy Software Products, all rights reserved.
``` 

A few searches over the internet weren't helpfull.

Any clues ?

---

