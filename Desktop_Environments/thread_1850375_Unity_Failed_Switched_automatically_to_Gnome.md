---
title: "Unity Failed Switched automatically to Gnome"
date: 2011-09-26
forum: Desktop Environments
---

### Post by awc_ on 2011-09-26
I'm not sure exactly what happened. I was running Unity just fine. After an upgrade some weeks ago Unity stopped working. There was a popup that told me what happened but I can't remember the exact words it used. Something to the effect that My computer doesn't support Unity and it would automatically switch to Gnome. 

(I've got an NVdia GTX460 as my video card and an overclocked AMD Phenom II 965 BE)

Help? (I've tried searching for related threads but can't find much)
```

/usr/lib/nux/unity_support_test -p
```Results in:
```

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  138 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x1ff
  Serial number of failed request:  32
  Current serial number in output stream:  32

```

---

### Post by collisionystm on 2011-09-26
Is this 11.04 or an 11.10 beta

---

### Post by awc_ on 2011-09-26
Forgot to mention that its 11.04

---

### Post by collisionystm on 2011-09-26
I would re-install your Nvidia drivers. 

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by maul9999 on 2011-09-26
> **awc_ said:**
> I'm not sure exactly what happened. I was running Unity just fine. After an upgrade some weeks ago Unity stopped working. There was a popup that told me what happened but I can't remember the exact words it used. Something to the effect that My computer doesn't support Unity and it would automatically switch to Gnome. 

(I've got an NVdia GTX460 as my video card and an overclocked AMD Phenom II 965 BE)

Help? (I've tried searching for related threads but can't find much)
```

/usr/lib/nux/unity_support_test -p
```Results in:
```

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  138 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x1ff
  Serial number of failed request:  32
  Current serial number in output stream:  32

```

It look like you have bad driver, you will want to reinstall from website or hardware driver update.

---

### Post by awc_ on 2011-09-26
I think I fixed it...

Fixed!

(To anyone paying attention,

I followed the afore mentioned advice, but installed an older driver rather than a newer one. Installing the newest driver fixed all of my problems, Unity now works just fine!

Thanks for the Help!)

---

### Post by collisionystm on 2011-09-27
Excellent. Be sure to mark this solved!

---

