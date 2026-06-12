---
title: "Mouse does not work in menu/desktop"
date: 2009-11-10
forum: Desktop Environments
---

### Post by x300 on 2009-11-10
I've got an old Dell X300 (12" screen) and thought that the netbook remix might fit my 1024x768 resolution quite nice. After installing everything seems to be working fine, except that I can't use my mouse for the desktop/desktop menu and the menu in the top left corner. The computer does not recognize my mouse clicks and it does not recognize anything when moving the mouse over the buttons. If i use alt+F2 to open firefox or use the keyboard arrows to open any program the mouse works perfectly fine.

I've tried googling this problem, but it gives me nothing. Does anyone have any suggestion for a solution?

---

### Post by Fully216 on 2009-11-12
I just installed ubuntu 9.10 netbook remix on a Sony Vaio PCG-4A1L and experienced the same problem.  The main menu has to be navigated using the tab key and arrows on the keyboard instead of the touchpad mouse.  Once an application is open, the mouse seems to work fine.  I am not sure if a bug report has yet been filed.  After searching the internet, I have not found a work around neither.

---

### Post by bandicot on 2009-11-22
I'm having this same problem with an IBM / Lenovo Thinkpad X40. Still searching for a solution.

---

### Post by x300 on 2009-11-22
It feels great to know that I'm not alone :)

I really hope someone finds a solution for this, cause I've given up on finding one myself.

---

### Post by bandicot on 2009-11-23
I found the following error repeated hundreds of times in .xsession-errors:

(netbook-launcher:1528): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed

This error appears to be associated with the problematic mouse/panel interaction. To confirm, I started a tail on .xsession-errors, exposed the desktop, and moused over all of the launcher panels on the left. Many more instances of the error are logged.

Following that clue, I found the following bug already logged against Clutter:
[https://bugzilla.redhat.com/show_bug.cgi?id=503251](https://bugzilla.redhat.com/show_bug.cgi?id=503251)

Seems like the right candidate. I'll keep digging for a resolution.

---

### Post by Cr0wley on 2009-12-08
Thank goodness for the community; I thought I was going mad!! The same issue occurs on my Dell Latitude X300. Anyone care to point me in the right direction of .xsession-errors so I can confirm I have the same events logged?

---

### Post by agalindo on 2010-01-06
Tagging along I have the same issue.

---

### Post by manderson1701 on 2010-03-27
Just to add my two cents - I have just installed the 9.10 UNR from CD  onto a dell d505. the USB install didn't work, it kept hanging while  unpacking crypto disks or something. 
Anyways, the mouse does not seem to action anything on the desktop but  will action the panel . You can navigate with the cursor keys except for  entering the favourites? therefore, You cannot det into Help !!!

---

### Post by Ambivalent on 2010-04-04
I'm having the same issue with a Dell Inspiron 1150 using both the build in trackpad button and a Logitech USB wireless mouse. If I rapidly move my mouse over the menu is sometimes registeres mousovers but never lets me click. I have to navigate by keyboard.

---

### Post by r1tch on 2010-04-06
> **bandicot said:**
> I found the following error repeated hundreds of times in .xsession-errors:

(netbook-launcher:1528): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed

This error appears to be associated with the problematic mouse/panel interaction. To confirm, I started a tail on .xsession-errors, exposed the desktop, and moused over all of the launcher panels on the left. Many more instances of the error are logged.

Following that clue, I found the following bug already logged against Clutter:
[https://bugzilla.redhat.com/show_bug.cgi?id=503251](https://bugzilla.redhat.com/show_bug.cgi?id=503251)

Seems like the right candidate. I'll keep digging for a resolution.

I had the same problem with clutter & the i915 video controller. There is a freedesktop.org bug about this, it mentions that MESA 7.7 will fix the problem -- included in Ubuntu 10.x, I guess.

Until then, a workaround: set env variable LIBGL_ALWAYS_SOFTWARE=1 -- which will make the program react slower, but it will at least become usable.

---

