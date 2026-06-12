---
title: "Help in upgrade Breezy to Dapper - mantain ati video driver"
date: 2006-08-03
forum: Desktop Environments
---

### Post by zeh on 2006-08-03
Hi everyone. I´ve installed Ubuntu 6.06 LTS but it freezes sometimes. I know that this is a bug with the ati/radeon driver. I´m running the OS on a Compaq Presario 2700T laptop with ATI Mobility Radeon M6 video chip with 16 Mb of dedicated memory.
Because of this annoyance, i´m back to breezy which runs like a breeze :) . Is there any way to upgrade to Dapper but maintaining the video drivers of Ubuntu 5.10? In fact, i just want to upgrade from Gnome 2.12 to 2.14. I think breezy is already a great desktop and i´ve heard many complaints about upgrading to dapper. Thanks!

---

### Post by kaffelars on 2006-08-03
I don't think you can keep the exact driver, because the driver's kernel module is kernel specific and Dapper uses a newer kernel than Breezy.

However, you should have 3D if you install the version of **linux-restricted-modules** package that matches the new kernel (when you have installed Dapper).

I believe that was all I did, and it worked. But maybe I'm just one of the lucky ones who hasn't had any major problems with Dapper:wink:

---

### Post by zeh on 2006-08-05
Thanx! I'll try to install this restricted modules.

---

### Post by zeh on 2006-08-07
Hi  kaffelars,

This restricted module that you´ve mentioned is the fglrx drivers?
If so, this solution won´t work for me...the radeon M6 isn´t supported by the ati fglrx proprietary driver...


> **kaffelars said:**
> I don't think you can keep the exact driver, because the driver's kernel module is kernel specific and Dapper uses a newer kernel than Breezy.

However, you should have 3D if you install the version of **linux-restricted-modules** package that matches the new kernel (when you have installed Dapper).

I believe that was all I did, and it worked. But maybe I'm just one of the lucky ones who hasn't had any major problems with Dapper:wink:

---

