---
title: "firefox artwork?"
date: 2005-08-26
forum: Desktop Environments
---

### Post by uperjer on 2005-08-26
when i start firefox, i get this message:

"The file /usr/share/ubuntu-artwork/home/index.html cannot be found.  Please check the location and try again."

anyone know where i can find this file?

---

### Post by FLeiXiuS on 2005-08-26
sudo apt-get install ubuntu-artwork

That should be the appropriate fix.

---

### Post by BlueNoteMKVI on 2005-10-24
I have the same problem.  I have tried the fix suggested by Flexius.  The package installed without errors, but the error message still persists when running FireFox.  Any ideas?

I'm running Kubuntu Breezy for AMD64.  I've only had it installed for a few days and have not changed much at all.

---

### Post by alb on 2005-11-17
I got the same message, but it's not due to ubuntu-artwork.

Firefox is trying to show an html page which is not there any more, after upgrading to breezy.

You can check this editing the firefox preferences, and setting another starting page. You can even browse to /usr/share/... you will see that index.html is not there, I have an ubuntu-index.html instead.

let us know...

---

### Post by shawnz on 2005-11-26
From the ubuntu-artwork changelog for breezy:

[INDENT]ubuntu-artwork (0.2.25-1) breezy; urgency=low

  * New upstream release
    **- removed browser homepage**
    - updated to breezy splash and wallpaper

 -- Jeff Waugh <jeff.waugh@ubuntu.com>  Fri, 30 Sep 2005 06:06:00 +1000[/INDENT]

Wouldn't understand why though :confused:

---

