---
title: "Error / unresponsiveness when detaching / reattaching screen"
date: 2006-01-13
forum: General Help
---

### Post by horsefactory on 2006-01-13
Hi.
Every time I detach or reattach screen either locally or via SSH, I get a short pause followed by:

/var/run/utmp: Interrupted system call

I've lost no functionality and screen works just fine but it's a little annoying. I've been told it could be an issue with irssi .8.10 which I do have running constantly, though i've found nothing myself. Any ideas how I can fix this folks?

---

### Post by Mr_Grieves on 2006-01-13
I can't make sense of it.. but this might be a clue..

> 
NAME
       utmp, wtmp - login records

SYNOPSIS
       #include <utmp.h>

DESCRIPTION
       The utmp file allows one to discover information about who is currently
       using the system.  There may be more users currently using the  system,
       because not all programs use utmp logging.


---

