---
title: "Display freezing with open ati drivers and 380X"
date: 2016-01-25
forum: Desktop Environments
---

### Post by PurposeOfReason on 2016-01-25
It usually takes a few hours after a fresh boot but my display will go unresponsive with kUbuntu using the kernel 4.2 (hoping it would fix the issue from stock). I can switch to a tty during the time and kill anything from there but it will no reflect once moving back to the GUI. Would much prefer to stick to the open drivers if at all possible.

---

### Post by QIII on 2016-01-25
Is this an R9 380X?

---

### Post by PurposeOfReason on 2016-01-26
Yes it is.

---

### Post by QIII on 2016-01-26
I did some testing on the R9 290X recently and reported my findings in my blog.  That has been a few months, but likely still applies.

It takes some time for the open sources developers to work with the AMD engineers on the open source driver.  So the open source driver may not have caught up to these newer adapters.

While I understand the sentiment, sticking to the open source drivers is not always pragmatic.

That said:  It is not certain that you issue has anything at all to do with the adapter or the driver.  But diagnosis often involves ruling out.  In this case, we may be able to rule out the adapter/driver if you would install the proprietary driver and attempt to use that as you have been using the open source driver.

---

