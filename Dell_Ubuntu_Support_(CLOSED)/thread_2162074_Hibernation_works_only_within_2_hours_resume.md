---
title: "Hibernation works only within 2 hours resume?"
date: 2013-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MarDio on 2013-07-13
Hello all, tried searching but search tool got me!
I've got a Dell Inspiron 6400 vintage sunburst (just to say its OLD) and everything is working fine, EXCEPT hibernating, it only works fine if you resume within 2 hours(approx) if you try to do this after a longer period (say after a workday) screen just blinks!
Now as far as I know hibernation doesnt use power and just saves state to drive, so what gives?
Doesnt matter since computer boots up in like 24 seconds but hey, would like to know if this has been addressed before and any workaround is wisely guarded somewhere.

Oh running 12.04, just love Unity!

Thanks!

---

### Post by carl4926 on 2013-07-13
Personally I never use hibernate, only ever Suspend. As my machine is connected to the AC. And even my netbook, which often isn't on AC power, I just Suspend, and it can like that all day with no issue.

---

### Post by lah7 on 2013-07-31
Do you have any specific programs that might be interfering with resuming after long hours?

I know that if I was to suspend with a certain app running, it'll crash and bring up the error report dialog after resuming, so it may be a package on your system that's interfering or doesn't like jumping time...

---

### Post by Whoopie on 2013-08-03
I can see the same behaviour with my Dell Vostro V131 since I upgrade to xorg-xserver-lts-raring and linux-generic-lts-raring.

Do you see a "BUG: soft lockup - cpu#0 stuck for ..." on resume?

---

