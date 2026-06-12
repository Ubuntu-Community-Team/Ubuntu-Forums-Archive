---
title: "Which Driver For nVidia is Installed?"
date: 2009-08-20
forum: Desktop Environments
---

### Post by CarlosinFL on 2009-08-20
When I go to the 'Restricted Drivers' menu & download the 'NVIDIA accelerated graphics driver' from the GUI menu, can someone tell me which specific packages it installs as if I were in 'terminal' and was using the apt-get utility to install manually?

Thanks!

---

### Post by Bachstelze on 2009-08-20
nvidia-glx-<driver_version>

You can check exactly which version you have with

```
sudo dpkg -l | grep nvidia-glx
```

---

### Post by CarlosinFL on 2009-08-20
Thanks!

---

