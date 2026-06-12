---
title: "mounting external hard drive"
date: 2009-06-07
forum: General Help
---

### Post by Idefix82 on 2009-06-07
My external hard drive used to automount upon plugging it in, but it has stopped doing that. How do I mount it? I can't see it under /dev, but lsusb returns
```
Bus 002 Device 002: ID 1058:0704 Western Digital Technologies, Inc.
```

This is the device I want to mount. It's formatted as Ext3. Why could the automount have stopped working?

---

### Post by merlinus on 2009-06-07
You might try looking under /media

Also try

```

mount

```

---

### Post by Idefix82 on 2009-06-07
It wasn't there under /media and /mount didn't show anything. In fact, I couldn't even see it with fdisk -l. Strangely, I now plugged it into a different usb slot (my third attempt) and it was recognised. Weird! Even more weird is that Vista was recognising it in any usb slot.

---

### Post by merlinus on 2009-06-07
Yeah.  To really screw things up, you need a computer!

Glad it is working....

---

