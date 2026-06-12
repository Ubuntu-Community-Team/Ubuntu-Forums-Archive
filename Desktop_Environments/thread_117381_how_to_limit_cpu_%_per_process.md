---
title: "how to limit cpu % per process"
date: 2006-01-14
forum: Desktop Environments
---

### Post by bmichel on 2006-01-14
Hi,

I'm using Qemu to run winXP/win2k/win98 and it's working nicely. My only issue so far is the amount of cpu % consumed.

Qemu allows me to define a max amount of memory dedicated for the guest OS but I don't know how to limit cpu usage for Qemu itself. 

Is there some command that I can launch in my script shell to limit Qemu or whatever linux process?

Thanks

---

### Post by Azion on 2006-01-14
Not too sure I haven't seen anything anyway.
Not too sure if it'd be a good idea to limit Qemu, as other important process may run under it

---

### Post by Mr_Grieves on 2006-01-14
You may run a process with 'nice'. But that does not seem to be what you're looking for.

```

man nice

```

---

