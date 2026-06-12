---
title: "Removing server kernel that appear unintentionally"
date: 2009-01-04
forum: General Help
---

### Post by inspired on 2009-01-04
Hi folks,
I was installing a bunch of software onto my new Ubuntu 8.10 install.

Things like virtualbox, Xen3, various themes, etc.

When I rebooted a new option had appeared in the Grub menu. It is:
Ubuntu 8.10, kernel 2.6.27-9-server


Ubuntu 8.10, kernel 2.6.27-9-server (recovery mode)


If I choose that option it will come back with an error. I forget what the error was now, but basically I can't boot into it, nor did I intend for it to be there... in that I did not intentionally install kernel 2.6.27-9-server

Looking at the package install logs it would appear it was installed whilst I installed Xen. Does that means Xen needs this?

Is there some way I can remove this extra server kernel?
The kernel I am using is: kernel 2.6.27-9-generic

**UPDATE**: Okay... I've now figured out I can find these kernels in the Package manager. Is there any harm in removing a kernel that I am not using? I also notice that when Ubuntu updated itself recently it installed 2.6.27-9 (which is what I now boot into) but it left 2.6.27-7 there. Can I remove the -7 one?

With thanks,

Jonathan

---

### Post by albinootje on 2009-01-04
> **inspired said:**
>  I also notice that when Ubuntu updated itself recently it installed 2.6.27-9 (which is what I now boot into) but it left 2.6.27-7 there. Can I remove the -7 one?


You can check which one you're using, to be 100 % sure 
(Sometimes after a kernel update, Grub in Ubuntu does no longer use the "default 0" line, but boots an older kernel instead :| )

```

uname -a

```
And yes, you can delete the older ones.

---

### Post by inspired on 2009-01-07
> **albinootje said:**
> You can check which one you're using, to be 100 % sure 
(Sometimes after a kernel update, Grub in Ubuntu does no longer use the "default 0" line, but boots an older kernel instead :| )

```

uname -a

```
And yes, you can delete the older ones.

Thanks a lot. Looks like it's using the new one. I'll delete the old one.

As for the server one... I guess I'll leave that there for now. I didn't get Xen working at this point... which is what installed the server kernal as far as I can tell.

Cheers,
Jonathan

---

