---
title: "Drop down menus stopped working in Okular and Firefox."
date: 2018-07-12
forum: Desktop Environments
---

### Post by sowani on 2018-07-12
After updating my Ubuntu 16.04.4 LTS on 10.Jul.2018, drop down menus in Okular and Firefox have stopped working. For example, in Okular, if I clicked on "File", nothing happens. Same thing happens in Firefox. When I click on any of the menu option, nothing happens, no menu is shown. Has anybody observed this problems recently? Is there any remedy for this? Thanks!

---

### Post by sowani on 2018-07-12
I traced this problem to "Compositor Settings for Desktop Effects". If I set rendering backend to OpenGL 2.0 or OpenGL 3.1 I observe this issue. XRender works fine. Considering recent updates I suspect this is a regression.

---

### Post by wollyjam on 2018-07-12
I have the same issue and XRender works fine here as well. I would never have found that - thanks a lot!

---

### Post by sowani on 2018-07-16
Sure @wollyjam... You may also want to subscribe to this: [https://answers.launchpad.net/ubuntu/+question/670844](https://answers.launchpad.net/ubuntu/+question/670844) so that you'll get a notification when and if this bug is fixed.

---

