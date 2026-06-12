---
title: "TRouble with xserver-xgl"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by mity on 2007-10-27
running 7.10
ATI RADEON

i am trying to get compiz to work. one of ther steps is to install xserver-xgl.

when i type in " sudo apt-get install xserver-xgl", i get this:


"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xgl: Depends: libglitz-glx1 but it is not installable
               Depends: libglitz1 (>= 0.4.3+cvs20050728) but it is not installable
E: Broken packages"

how do i fix the package?

thank you.

---

### Post by itsbradman on 2007-10-27
try sudo apt-get install -f

---

