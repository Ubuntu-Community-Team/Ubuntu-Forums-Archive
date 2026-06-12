---
title: "application switcher is missing icons"
date: 2008-11-02
forum: Desktop Environments
---

### Post by carpeme on 2008-11-02
When alt-tabbing through windows, the application icon which usually appears at the bottom right corner is missing (screenshot attached). This happens when visual settings are set to either "normal" or "extra", but the icons work fine when visual settings are set to "none", so the icon is there somewhere (right?). I think some people have reported that sometimes particular icons are missing, but all icons are missing for me. If anybody can offer any advice, either how to fix this or even how to track down what the problem is, I'd be very grateful.

---

### Post by arcani on 2008-11-10
I have the same problem.  Anybody have a solution?

---

### Post by carpeme on 2008-11-10
arcani, it turned out to be due to my video card driver. The ATI driver (at least for me) is not there yet. I uninstalled that, and the icons appeared. I wish I understood more, but I imagine I'll just be waiting until the driver situation fixes itself, somehow.

---

### Post by wenzlicker on 2008-11-14
I have the same problem. I've switched the application switcher to the ring switcher. For whatever reason, the ring switcher works.

To do this, use the CompizConfig Settings Manager. Under Window Management, uncheck Application Switcher and check Ring Switcher. Lastly, change the Key bindings to <alt>Tab and <Shift><Aalt>Tab for next window and previous window.

NOTE: I also tried the Static Application Switcher, and had similar results to the Application Switcher.

---

### Post by sandyscott on 2008-12-11
I had exactly this problem, but fixed it by disabling the mipmap option. Works for both Application Switcher and Static Application Switcher

---

