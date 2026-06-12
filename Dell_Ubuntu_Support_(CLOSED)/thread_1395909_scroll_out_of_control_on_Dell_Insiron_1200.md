---
title: "scroll out of control on Dell Insiron 1200"
date: 2010-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lakelovers on 2010-02-01
I'm running 9.10 on a Dell Insiron 1200 laptop and I can't control the scrolling. As I scroll down a page, it runs away and I'm unable to stop the scroll until it reaches the page bottom. How can I fix this?

---

### Post by bobcollard on 2010-02-04
> **lakelovers said:**
> I'm running 9.10 on a Dell Insiron 1200 laptop and I can't control the scrolling. As I scroll down a page, it runs away and I'm unable to stop the scroll until it reaches the page bottom. How can I fix this?
Install gsynaptics a touch pad control. Put it in your startup to get it working right away.  You can also turn off the touchpad if you are using a mouse.  You can find it in Synaptic Package Manager or install it from the Command line with "sudo apt-get install gsynaptics" (without the quotes.)  After installing, uncheck the boxes for touchpad under System Settings/Keyboard and Mouse, you cannot run both at the same time.

---

### Post by lakelovers on 2010-02-04
Thanks, I'll give a try.

---

