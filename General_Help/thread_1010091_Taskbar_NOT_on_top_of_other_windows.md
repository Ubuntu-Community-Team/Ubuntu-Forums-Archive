---
title: "Taskbar NOT on top of other windows ???"
date: 2008-12-13
forum: General Help
---

### Post by Thomas_VDB on 2008-12-13
Hi,

I am pretty new at ubuntu. I am porting an application from Windows to Ubuntu.
In that application, I set the user-interface window full screen. In Windows, it works okay : the user-interface window comes on top of the taskbar.
In ubuntu, the taskbar (applications, places, system,...) always stays visible.
Is there an option like in Windows "keep taskbar on top of other windows", that I can switch off.
I've also tried the "Autohide"-option, but this doesn't work as well, because the taskbar still apears when moving the cursor to the bottom of the screen. I want my app to be really full screen all the time.
Thanks.
Thomas

---

### Post by Wartender on 2008-12-13
you can hide the taskbar; in properties select the show hide buttons option, and click them, your taskbar will hide and windows will be on top of it.

---

### Post by fubbleskag on 2008-12-13
I've probably collected about 12 hours of googling towards this end with no results. The closest I've come was when someone suggested using xprop to change the value of _NET_WORKAREA - after a few hours of googling how to use xprop properly (gah, formats!), it turned out that changing this value didn't have the desired effect anyway.

---

### Post by Thomas_VDB on 2008-12-13
Hi Wartender,

You're solutions is no good, because I do'nt want the users to be able to access the taskbar. With the hide-button, the can unhide the taskbar.

How is it possible that there is no solution? Other apps, e.g. games are able to get in front of the taskbar.

Thomas.

---

