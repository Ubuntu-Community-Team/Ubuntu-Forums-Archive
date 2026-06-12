---
title: "A problem with updates or what?"
date: 2009-01-30
forum: General Help
---

### Post by reprobus on 2009-01-30
Over the last 3 days I've installed 2.6.27-11-generic 3 times now as it has showed up in the updates manager 3 times. Have they had problems with it and fixed it a few times now and reissued it or is my box on crack?

---

### Post by cariboo on 2009-01-30
Are you sure it is installed? In a Applications-->Accessories-->Terminal type:

```
uname -a
```

you should get a result that looks something like this:

```
Linux chilanko 2.6.22-1-mepis-smp #1 SMP PREEMPT Mon Feb 18 21:44:02 EST 2008 i686 GNU/Linux
```

The kernel version number will be different from the above example, as at the moment I'm running AntiX.

What you are seeing may just be dependencies that are needed to install the kernel.

Jim

---

### Post by icanfly0307 on 2009-01-30
I don't think that you installed the 2.6.27-11 kernel three times. In the update manager, a kernel update comes up as three parts:

1. Restricted modules (restricted-modules-2.6.27-11)
2. Kernel Image (linux-image-2.6.27-11)
3. Kernel Headers (linux-headers-2.6.27-11)

So basically, you installed three parts of one entire kernel.

And no your computer isn't on crack... :lolflag:

---

### Post by reprobus on 2009-01-30
Linux Linux 2.6.27-11-generic #1 SMP Wed Jan 28 00:02:01 UTC 2009 i686

Yeah I know it comes in three parts. I've installed the 2.6.27-11-generic packages three times now because it has kept showing up in the update manager even after its already been installed and I have confirmed it was installed with uname -a

---

