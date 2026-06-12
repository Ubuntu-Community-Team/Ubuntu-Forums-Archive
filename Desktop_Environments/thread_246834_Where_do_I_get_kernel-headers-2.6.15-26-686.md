---
title: "Where do I get kernel-headers-2.6.15-26-686?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by erikcw on 2006-08-29
Hi,

I'm trying to get "kernel-headers-2.6.15-26-686".  But it's not working.

> 
erik@turbo:/etc/apt$ sudo apt-get install kernel-headers-`uname -r` build-essential
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-headers-2.6.15-26-686
erik@turbo:/etc/apt$


What do I need to put in my sources.list to get these headers?

Thanks!

---

### Post by cstudent on 2006-08-29
I believe you want linux-headers not kernel-headers

---

### Post by erikcw on 2006-08-29
You were right!  linux-headers did the trick!!

Thanks!

---

### Post by cstudent on 2006-08-30
Every now and then I get one right. :)

---

