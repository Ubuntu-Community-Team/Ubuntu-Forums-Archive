---
title: "Driver for Intel Graphics Card"
date: 2006-08-26
forum: Desktop Environments
---

### Post by Eleka on 2006-08-26
Hello people

I have a laptop with a Intel integrated video card and a wide screen.

I want to have correctly loaded the video driver, but I don't know if it's working now.

I have the i810 module loaded (it appears in lsmod | grep i810) and in glxinfo I have direct rendeering yes ... but with glxgears I only have round 500 FPS ... it's really poor, doesn't?

My lspci | grep VGA output is that:
```
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
```

If somebody have the same video card in his/her laptop and have a little time, can you post your FPS number with glxgears?

I want to make it work, but I can't!

---

### Post by kaptan on 2006-08-26
I don't have the same card but it may have something to do with the BIOS firmware. I recently installed Dapper Drake on a Dell Inspiron 2600, I had to downgrade firmware from A11 to A6.

---

### Post by defeca on 2006-08-26
I have the same card, and until today I had about 800 FPS.
But after today's update I started having this error:

```
libGL warning: 3D driver claims to not support visual 0x5b
glxgears: intel_ioctl.c:62: intelEmitIrqLocked: Assertion `((*(int *)intel->driHwLock) & ~0x40000000U) == (0x80000000U|intel->hHWContext)' failed.
Aborted
```

And thw windows don't show the borders anymore.

---

### Post by PathSpace on 2006-08-26
I have the same type of graphics card, but nothing appears at all when I do lsmod | grep i810.  :(   What's wrong?  :confused:

---

### Post by Eleka on 2006-08-26
PathSpace, I think that you are not using the module i810 ... perhaps you are running vesa or other ....

kaptan: how can I know wich version of firmware I have?

---

### Post by kairu0 on 2006-08-29
> **defeca said:**
> I have the same card, and until today I had about 800 FPS.
But after today's update I started having this error:


Exactly the same problem here. I think this has less to do with a firmware version than another faulty update. Has anyone been able to resolve this?

---

