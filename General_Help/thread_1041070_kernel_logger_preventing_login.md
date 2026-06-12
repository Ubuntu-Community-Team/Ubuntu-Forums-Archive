---
title: "kernel logger preventing login"
date: 2009-01-16
forum: General Help
---

### Post by dnoyeb on 2009-01-16
I found the issue that is preventing loging into my system after about a day.  Its the kernel logger klogd.  All of my logins hang.  From the terminal they hang in such a way that they can not be recovered.  But typing login at a prompt hangs as well but it can be killed.

restarting klogd fixes the issue until it happens again.

Anyone else seen this issue?

(im 90% positive this is from the kernel logger restart and not the system logger restart)

---

