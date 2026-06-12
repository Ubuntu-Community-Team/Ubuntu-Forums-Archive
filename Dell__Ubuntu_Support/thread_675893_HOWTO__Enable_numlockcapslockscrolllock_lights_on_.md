---
title: "HOWTO:  Enable numlock/capslock/scrolllock lights on a laptop"
date: 2008-01-23
forum: Dell  Ubuntu Support
---

### Post by tr333 on 2008-01-23
Tested on:  Dell Inspiron 1520 with Ubuntu Gutsy Gibbon 7.10

If you are using Ubuntu on a laptop, you might find that the numlock, capslock, and scrolllock lights on the laptop itself do not work, even if they work on an external keyboard.  The solution for this is to remove the *mouseemu* package.  Mouseemu provides similar (but limited) functionality to what synaptics does in the way of trackpad actions, so removing this will not cause any issues if you're using synaptics for the trackpad/mouse.

Mouseemu bug information:  [https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/103375](https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/103375)

---

### Post by K.Mandla on 2008-01-23
Moved to Dell Ubuntu Support.

---

