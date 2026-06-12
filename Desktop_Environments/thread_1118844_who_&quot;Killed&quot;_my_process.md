---
title: "who &quot;Killed&quot; my process?"
date: 2009-04-07
forum: Desktop Environments
---

### Post by sbq on 2009-04-07
Greetings,

My application runs as a background process on Ubuntu.  It is currently started at the command line in a Terminal window.

Recently a user was executing the application for a while and it died mysteriously.  The text:

Killed

was on the terminal.  This happened two times.  I asked if someone at a different Terminal used the kill command to kill the process?  No.

Under what conditions would Linux/Terminal decide to kill my process and cause "Killed" to be displayed?

-Sam

---

### Post by Vadi on 2009-04-07
It might've went haywire on memory and the kernel killed it.

---

### Post by sbq on 2009-04-07
> **Vadi said:**
> It might've went haywire on memory and the kernel killed it.

That must have been what happened.  I wrote a program that malloc'd memory in an infinite loop.  The system got really slow, then "Killed" appeared in the terminal window and the process was terminated.  There were log messages written into /var/log/kern.log.

---

