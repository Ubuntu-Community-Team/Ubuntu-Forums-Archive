---
title: "System lockup at empty trash"
date: 2009-06-16
forum: General Help
---

### Post by gjtoth on 2009-06-16
This has happened 3 times now so it's a relatively consistent occurrence.  I attempt to empty trash and within 2 seconds the system locks up.  Anyone else have this?

---

### Post by Uzi304 on 2009-06-16
Are you using Ext4?

---

### Post by gjtoth on 2009-06-16
> **Uzi304 said:**
> Are you using Ext4?

Yup...  sure am.

---

### Post by renkinjutsu on 2009-06-16
that's a problem ext4 had for a while
but to my understanding, it should have been fixed already.. do you have any pending kernel updates?

---

### Post by gjtoth on 2009-06-16
> **renkinjutsu said:**
> that's a problem ext4 had for a while
but to my understanding, it should have been fixed already.. do you have any pending kernel updates?

Just ran an update and have NO updates pending.  What is the latest kernel out?  Also, I forgot the command to find out what version I'm running.  Got that handy?

<edit>  The command is "uname -r"  I'm running 2.6.28-13-generic.  That's the latest one out, right?

---

### Post by gjtoth on 2009-06-16
The kernel must have gotten corrupted somehow.  I reinstalled it, rebooted, and everything is cool.

---

### Post by renkinjutsu on 2009-06-20
good to hear your kernels are doing fine now ;)
sorry, I was away from my computer (actually from home) for a period of time
and for checking your version of linux, try ```
uname -r
```
that command gives all kinds of information about your machine given the right options, but -r should give you your version number.

---

