---
title: "How to disable input hotplugging created device?"
date: 2009-02-12
forum: General Help
---

### Post by Kaan_ on 2009-02-12
I got my sixaxis gamepad working using bluetooth but the evdev input driver automatically creates a /dev/input/event7 device and assigns left analog as mouse. Is there any way to prevent this?

lshal -m prints:

```
Start monitoring devicelist:
-------------------------------------------------
20:51:11.508: bluetooth_acl_1bfb2757df added
20:51:12.365: usb_device_a12_1_noserial_if0_logicaldev_input added
```

Thanks

---

