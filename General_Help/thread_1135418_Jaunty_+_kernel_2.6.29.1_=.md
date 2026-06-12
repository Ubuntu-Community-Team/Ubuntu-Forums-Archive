---
title: "Jaunty + kernel 2.6.29.1 = ?"
date: 2009-04-24
forum: General Help
---

### Post by sgtbug on 2009-04-24
Hi guys

Downloaded and installed the 2.6.29.1 kernel from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/").

Anyone else using it? Any problems anyone has faced till now?

Please post your opinions..

---

### Post by sdennie on 2009-04-24
The kernel is usually very interchangeable.  I've been using 2.6.29.1 on Hardy and have no problems to report.

---

### Post by sgtbug on 2009-04-24
so the pre-compiled kernels at kernel.ubuntu.com are ubuntu specific or for any debian based system? moreover, are they configured exactly as the stock 2.6.28-11 in jaunty?

---

### Post by sdennie on 2009-04-24
> **coolaks said:**
> so the pre-compiled kernels at kernel.ubuntu.com are ubuntu specific or for any debian based system? moreover, are they configured exactly as the stock 2.6.28-11 in jaunty?

It's unlikely that they are Ubuntu specific.  I'm not sure how they are configured but, you could diff the configs (in /boot) and find out what the changes are.

---

### Post by sgtbug on 2009-04-24
i will check that for sure.. but i do notice faster disk performance.. i guess that could be a first.. would u advice a 2.6.28-11 removal.. ? ;-)

---

### Post by sdennie on 2009-04-24
> **coolaks said:**
> i will check that for sure.. but i do notice faster disk performance.. i guess that could be a first.. would u advice a 2.6.28-11 removal.. ? ;-)

If you aren't actively using a kernel, the only badness it's causing your machine is a small amount of disk space is being taken up.  It's also good to always have a known working kernel around in case something bad happens.  So, no, I wouldn't remove it.

---

### Post by DougieFresh4U on 2009-04-24
> **coolaks said:**
> Hi guys

Downloaded and installed the 2.6.29.1 kernel from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.1/").

Anyone else using it? Any problems anyone has faced till now?

Please post your opinions..

You may want to check .30rc3. Seems to run just great except I can't use 'fglrx' :(

---

### Post by sdennie on 2009-04-24
> **DougieFresh4U said:**
> You may want to check .30rc3. Seems to run just great except I can't use 'fglrx' :(

I actually wouldn't recommend low number rc releases of the kernel unless you are purposely testing them and plan to give feedback or are developing them.  The later rc releases are probably just fine but, even then, you may have problems with 3rd party drivers.

---

### Post by Ticketoride on 2009-04-24
I hear Linus Torvald is still in there writing and moving the Kernel Development along, so I would doubt it would be specific to any Linux Flavour.

---

### Post by sgtbug on 2009-04-24
its a precompiled deb so i guess it is limited to the debian family at least..

---

