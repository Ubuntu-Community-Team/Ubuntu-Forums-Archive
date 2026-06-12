---
title: "Multi-head, Multi-user in 8.10"
date: 2008-11-25
forum: Desktop Environments
---

### Post by Milkman on 2008-11-25
I've got a machine with two monitors, keyboards and mice which I would like to become a multi-head, multi-user machine.  I've read around plenty of (old) examples of doing this (and I even had it working a few years ago) and it all seems quite simple, but...

Since xorg's moved to use HAL for detecting / configuring its inputs (rather than xorg.conf) I'm not sure how to configure my layouts.  I've even tried to add the following to my xorg.conf but it seems to have no effect.

```
Section "ServerFlags"
    Option "AutoAddDevices" "off"
EndSection
```

Can anyone give me some suggestions / pointers about setting up this multi-head, multi-user environment with all these crazy *advancements*?

---

### Post by Martje_001 on 2008-12-21
I'm also looking for this. Anyone?

Edit: OK, I've found [Userful Multiplier]("http://www2.userful.com/products/userful-multiplier") but it's only free up to 2 seats..

---

### Post by Milkman on 2008-12-28
Have you had any luck configuring userful?  I had a play with the version in the repo and it did not seem to work correctly :(

---

### Post by Martje_001 on 2008-12-28
> **Milkman said:**
> Have you had any luck configuring userful?  I had a play with the version in the repo and it did not seem to work correctly :(
Me n'either. I use AMD64 so it will not work...

---

