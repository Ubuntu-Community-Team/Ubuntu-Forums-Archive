---
title: "[SOLVED] apt-get remove dependencies?"
date: 2006-02-16
forum: Desktop Environments
---

### Post by antiemptyv on 2006-02-16
When Iinstall a programwith apt-get, it displays applications upon which my desired application depends.  I give apt-get a big OK, and it installs all it needs to. That's great...

Here's my question:  If and when I decide that the application is not for me, how do I remove all the applications (i.e. the dependencies) that were needed to run the initial application?

Can I do this through apt-get, or do I need to save a list of all the dependencies that were downloaded and remove them one-by-one?

Thanks.

---

### Post by alfonz on 2006-02-17
```
apt-get remove --purge <application name>
``` is what you are looking for I believe.

---

### Post by heimo on 2006-02-17
Xians instructions on how to remove orphaned packages:
[http://www.ubuntuforums.org/showpost.php?p=279036&postcount=11](http://www.ubuntuforums.org/showpost.php?p=279036&postcount=11)

---

### Post by antiemptyv on 2006-02-17
but wil that remove dependencies that other applications depend on?

---

### Post by alfonz on 2006-02-17
no it shouldn't

---

### Post by RAOF on 2006-02-17
A simple (but not retroactive) way to do what you want is to use "aptitude".  It's a combination of apt-get & apt-cache.  You can
"aptitude search package" to find packages, "aptitude show packagename" to show details about a package, and "aptitude install foo"/"aptitude remove foo".

Best of all, it marks any dependencies it automatically installs as "automatic".  When you remove a package, and there is now an "automatic" package which nothing else depends on, it also removes the automatic package.

This, however, **only** works for things you've installed through aptitude.  For stuff you've already done, deborphan/gtkorphan should work.

---

### Post by antiemptyv on 2006-02-17
Awesome.  I'll try that tomorrow.

I'm asking because I've recently moved to OpenBox (at least temporarily), and I was looking for a good docking application.  I of course like the Mac look, but is certainly not required.  I installed perlpanel, and it wasn't doing it for me.

I hope it turns out fine. Thanks for the speedy replies.

Matt

---

