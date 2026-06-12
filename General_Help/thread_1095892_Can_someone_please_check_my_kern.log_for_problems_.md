---
title: "Can someone please check my kern.log for problems with suspend?"
date: 2009-03-14
forum: General Help
---

### Post by pavsid on 2009-03-14
Hi, wondered if someone could check the attached log taken from kern.log immediately after putting pc into suspend mode - i have the problem where pc immediately wakes once in suspend mode and trying to find out the cause.

On line 59 is the following error:

Mar 14 12:55:27 pav-ubuntu kernel: [  274.910950] ACPI: Unable to turn cooling device [f741e6a8] 'off'

i found a thread elsewhere which recommended the following fix:

```
mmod thermal; modprobe thermal
```

but wanted to check that it's safe and if so, where/how do i implement it?

Or, if anyone has any other solutions....??

Thanks

---

### Post by pavsid on 2009-03-14
Forget it, i found the solution to the computer immediately waking from suspend mode [here]("http://www.gossamer-threads.com/lists/mythtv/users/316830#316830")

not too bothered about the error in kern.log now, it only appears once anyway not numerous times like others have reported.

---

