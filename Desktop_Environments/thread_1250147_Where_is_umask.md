---
title: "Where is umask?"
date: 2009-08-26
forum: Desktop Environments
---

### Post by Albert Li on 2009-08-26
Hi,

I installed Ubuntu 9.04 inside of Windows XP. Now I found that there is no umask command. I belief umask is a basic command in Unix. How to install it?

Any information would be appreciated. Thanks in advance.

---

### Post by lswb on 2009-08-26
umask is a builtin command of the shell (bash) You can set it on the command line or in ~/.profile, or in /etc/profile for system default.

---

### Post by Albert Li on 2009-08-26
> **lswb said:**
> umask is a builtin command of the shell (bash) You can set it on the command line or in ~/.profile, or in /etc/profile for system default.

Thanks.

---

### Post by Albert Li on 2009-08-26
> **lswb said:**
> umask is a builtin command of the shell (bash) You can set it on the command line or in ~/.profile, or in /etc/profile for system default.

Now, I have a second question: How to call umask in other program, for example in Java? It is not a "standalone" command.

---

