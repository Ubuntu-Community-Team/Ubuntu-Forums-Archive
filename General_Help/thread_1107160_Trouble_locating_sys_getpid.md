---
title: "Trouble locating sys_getpid"
date: 2009-03-26
forum: General Help
---

### Post by NuNn DaDdY on 2009-03-26
I am trying to find the sys_getpid function so I can edit it for an assignment which I have in a class.  But I am having trouble locating this file; when I look at the system call table I see the system call number for getpid is 20 but I cannot find the file that the system call is located within.  I have done some research online and it has pointed to "kernel/sched.c" but when I find the file(s) that I believe to be this there is no such function located within similar to what they have online.

---

### Post by hooverdn on 2009-03-27
I read elsewhere (cannot vouch for it) that

   sys_getpid() 

just returns

   current->tgid

and that seems to work without linking any special libraries. 

Best,

Dog

---

