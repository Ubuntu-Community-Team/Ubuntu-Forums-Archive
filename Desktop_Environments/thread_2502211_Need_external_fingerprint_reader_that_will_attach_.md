---
title: "Need external fingerprint reader that will attach to an ASUS PN50"
date: 2024-11-05
forum: Desktop Environments
---

### Post by acag on 2024-11-05
I would like to attach an external fingerprint reader to my ASUS PN50 mini desktop computer. I am running Ubuntu 24.04.1. Has anyone been able to successfully accomplish this feat?

---

### Post by 1fallen on 2024-11-05
It just has to be Linux Friendly.

[https://itsfoss.com/fingerprint-login-ubuntu/](https://itsfoss.com/fingerprint-login-ubuntu/)

There are posts here in UF that warn against it. (A search should show them)
It keeps a photo of your finger/thumb/toe what ever you chose as the scan. (Just a friendly heads-up) :)

This is key "libfprint" needs to be friendly to your device, not all work on Linux.

---

### Post by acag on 2024-11-05
Yep, I get it. I guess what I am looking for is a recommendation on what external fingerprint reader will work.

Regards,
Claude Godfrey

---

### Post by 1fallen on 2024-11-05
Older Elan readers are fully supported, along with those from major brands.
Readers which impose encryption protocols may not be recognized, so (since it can be difficult to find the chipset in use) you should really buy with reserve if you own GNU/Linux systems and explicit support is not declared in the specifications from the seller.

From Debian Supported: [https://fprint.freedesktop.org/supported-devices.html](https://fprint.freedesktop.org/supported-devices.html)

There are probably more that I'm not aware of currently, but that's a good start.

---

### Post by acag on 2024-11-12
Thanks for everything!

---

