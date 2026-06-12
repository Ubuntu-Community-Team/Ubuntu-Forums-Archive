---
title: "Brightness control hook"
date: 2011-09-19
forum: Desktop Environments
---

### Post by hekto5 on 2011-09-19
I'd like to use laptop brightness keys to control not only the laptop screen brightness, but also the external monitor brightness. It supports DDC/CI so

```
sudo modprobe i2c-dev
sudo ddccontrol -r 0x10 -w 20 dev:/dev/i2c-14
```

does the job.

Does anybody know how can I hook up to the brightness change event? It must be possible because many DEs are displaying notification.

---

