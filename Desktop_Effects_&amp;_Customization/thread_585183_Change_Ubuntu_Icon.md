---
title: "Change Ubuntu Icon"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by fedex1993 on 2007-10-21
is there anyway that i on gutsy that i can change the ubuntu menu button on the bar?

---

### Post by fedex1993 on 2007-10-21
*bump*

---

### Post by verbruggher on 2007-10-21
so no method do do this? ofcourse to make it even better.

How we change the ubuntu logo in the menubar?

---

### Post by A-1337 on 2007-10-21
> **verbruggher said:**
> so no method do do this? ofcourse to make it even better.

How we change the ubuntu logo in the menubar?

Download and install tango project icons source tarball from official site. You'll get a pair of shoes instead ubuntu logo.

---

### Post by verbruggher on 2007-10-22
thx, but what if I want something else then shoes? ;)

---

### Post by nquinnathome1 on 2007-10-22
Go to the folder of icons you're currently using and you must put an icon of your choice called 'distributor-logo' into /scalable/places of that icon folder, log out and back in and it should be done.

If you're using Gutsy, it's changed, and for the menu icon itself you need to add a file into that folder called 'start-here'

So for example:

/home/yourName/.icons/nameOfActiveIcons/scalable/places/start-here.png

I believe the image format can be whatever you want so long as it's understood by Ubuntu; png, svg, jpg etc. Icons should be a suitable size if you use your own; 48x48px is enough.

---

