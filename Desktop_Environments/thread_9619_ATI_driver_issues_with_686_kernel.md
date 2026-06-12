---
title: "ATI driver issues with 686 kernel"
date: 2004-12-30
forum: Desktop Environments
---

### Post by nehalem on 2004-12-30
So I had everything working under the 386 kernel, decided to upgrade to the 686 kernel, and under that kernel, for whatever reason, my external monitor does not work on my laptop.  I really would reather stick with the 686 kernel since it seems to work better overall.

I know in the tutorials it says to install the kernels first.  Is there some reason that it is important to do that and could that be why this stuff is not working right?

Thanks.

---

### Post by ulrich on 2004-12-30
hi, so this is a shot in the dark, but
are you talking about the fglrx-drivers (proprietary ati ) or the ones that come with xfree?
if you use the ati-drivers:
if you upgraded your kernel, did you also upgraded the **restricted modules** package for your kernel?
and if youre using the xfree-drivers:
shouldnt dpkg-reconfigure xfree-blah... do the trick?

hope this helps

ulrich

---

