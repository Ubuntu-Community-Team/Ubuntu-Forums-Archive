---
title: "libjpeg is broken -- how do I fix it?"
date: 2009-09-27
forum: Desktop Environments
---

### Post by foxmajik on 2009-09-27
Hello,

Recently I was messing around with swiftweasel and tried to install libjpeg7, which somehow broke the existing package.

Now any program that depends on rendering jpegs either crashes of won't display the image.

I have tried using sudo dpkg-reconfigure but that did not fix the problem.

I also tried removing libjpeg62 but when I try to do that the package manager wants to remove every other package that depends on it (which is several hundred packages).

How can I fix just the libjpeg62 package?

---

### Post by earthpigg on 2009-09-27
in synaptic, right click -> reinstall?

---

### Post by foxmajik on 2009-09-28
> **earthpigg said:**
> in synaptic, right click -> reinstall?

Thanks, that did it.

---

### Post by theZoid on 2009-09-28
> **earthpigg said:**
> in synaptic, right click -> reinstall?

:lolflag:

---

