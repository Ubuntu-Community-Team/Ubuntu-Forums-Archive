---
title: "Are run-levels being phased out?"
date: 2009-02-02
forum: General Help
---

### Post by randysparks on 2009-02-02
I understand that with the introduction of Upstart, run-levels would slowly be phased out, and all run-level-style tasks put into /etc/event.d. But on my 8.10 system, it's still a pretty traditional emulation of run-levels. 

What are the plans? Can anybody point me in the direction of a good source of materials to learn more about plans for Upstart in Ubuntu?

---

### Post by mb_webguy on 2009-02-02
From Wikipedia's article on run levels:> 
**Debian Linux**

Debian, as well as most of the distributions based on it, like early Ubuntu, does not make any distinction between runlevels 2 to 5.
Debian Linux runlevels ID 	Description
0 	Halt
1 	Single user mode
2-5 	Full multi-user with console logins and display manager if installed
6 	Reboot

**Ubuntu**

Ubuntu 6.10 (Edgy Eft) and later contain Upstart as a replacement for the traditional init-process, but they still use the traditional init scripts and Upstart's SysV-rc compatibility tools to start most services and emulate runlevels.

Here's a fairly informative article from Linux.com: [http://www.linux.com/feature/125977]("http://www.linux.com/feature/125977")

---

### Post by randysparks on 2009-02-03
> **mb_webguy said:**
> From Wikipedia's article on run levels:

Here's a fairly informative article from Linux.com: [http://www.linux.com/feature/125977]("http://www.linux.com/feature/125977")

Thanks for that, but the question remains: Are there plans to phase-out run-levels? I understood that this was one of the reasons Upstart was created.

---

### Post by mrsteveman1 on 2009-02-14
They probably will not phase out the runlevels, so at least as far as i know, you will always be able to stick a script in some directory and get it to run on startup.

What they said they plan to do, and i hope finish soon, is to port the scripts that come with the ubuntu repository packages so that they are native upstart scripts.

---

### Post by dcstar on 2009-02-14
> **randysparks said:**
> I understand that with the introduction of Upstart, run-levels would slowly be phased out, and all run-level-style tasks put into /etc/event.d. But on my 8.10 system, it's still a pretty traditional emulation of run-levels. 

What are the plans? Can anybody point me in the direction of a good source of materials to learn more about plans for Upstart in Ubuntu?

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

