---
title: "Kernel Hacking Issue"
date: 2009-03-31
forum: General Help
---

### Post by NuNn DaDdY on 2009-03-31
I recently added a printk statement to my timer.c file in /usr/src/linux-source-2-6-27/ so that each time SYS_GETPID was called I would have this printed out to my console and to my /var/log/messages file.  However, when I create a simple program which uses getpid() and run it I neither get anything printed to the console nor to the messages file.  The code for SYS_GETPID I put in is as follows:

```

asmlinkage long sys_getpid(void)
{
	printk(KERN_CRIT, "SYS_GETPID CALLED...\n");
	return task_tgid_vnr(current);
}

```

I recompiled my kernel and installed it again but am not sure why this isn't working.

---

### Post by NuNn DaDdY on 2009-03-31
Also, I just loaded a custom hello world module into the kernel successfully using the insmod function but this was not recorded to my /var/log/messages file.  Is there another location in Ubuntu where this file is loaded?

---

