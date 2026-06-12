---
title: "Logitech Dual Action Gamepad Help"
date: 2011-07-08
forum: Gaming &amp; Leisure
---

### Post by jessay9112005 on 2011-07-08
Hey, first time poster here. I have been trying to find any information I can find to where I can use my Logitech Dual Action gamepad on emulators on my OS (Xubuntu 10.04 LTS). Any information concerning how to make this gamepad work on here is greatly appreciated.

---

### Post by JerryWE on 2011-08-17
I am looking for the same thing I have the logitech dual action gamepad and would like to be able to use it in Ubuntu. Thanks

---

### Post by Grumbel on 2012-02-07
> **JerryWE said:**
> I am looking for the same thing I have the logitech dual action gamepad and would like to be able to use it in Ubuntu. Thanks
Almost all USB gamepads should work out of the box just by plugging them in. You can verify that they work by:

```
apt-get install joystick
jstest /dev/input/js0
```

---

