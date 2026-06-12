---
title: "Dell Studio Hybrid resolution problems"
date: 2009-06-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Upstartof77 on 2009-06-17
Hi guys,
 I'm having some issues with my Dell Hybrid 140G. Everything is working on it but the graphics. They work, only sort of though. I have image and some video support but I cannot get the drivers to support the poper display resolution. Instead of supporting the native 1440X900 of my monitor it puts it at 1152X864. I've tried to get new drivers and old. No difference. Tried modifying the xorg file but again to no avail. I'm out of ideas. Anyone have a suggestion?

Edit: After playing around with it some more I've figured something out. I think the problem is that I'm using a DVI to VGA adapter and it's making Ubuntu think there are two monitors. It sets the default monitor to the weird settings and not my actual monitor. Anymore suggestions on how to make Ubuntu recognize my actual monitor?

---

### Post by mynameinc on 2009-06-18
Ati?

---

### Post by mynameinc on 2009-06-18
> **Upstartof77 said:**
> Hi guys,
 I'm having some issues with my Dell Hybrid 140G. Everything is working on it but the graphics. They work, only sort of though. I have image and some video support but I cannot get the drivers to support the poper display resolution. Instead of supporting the native 1440X900 of my monitor it puts it at 1152X864. I've tried to get new drivers and old. No difference. Tried modifying the xorg file but again to no avail. I'm out of ideas. Anyone have a suggestion?

Edit: After playing around with it some more I've figured something out. I think the problem is that I'm using a DVI to VGA adapter and it's making Ubuntu think there are two monitors. It sets the default monitor to the weird settings and not my actual monitor. Anymore suggestions on how to make Ubuntu recognize my actual monitor?

Go to System->Preferences->Display->Detect Monitors
Hopefully, it will detect your default monitor, and you can turn it on, and then turn the resolution to 1440x900.

---

