---
title: "Enable DRI"
date: 2009-02-14
forum: General Help
---

### Post by graemejager on 2009-02-14
Alright, I've been looking around and I don't understand what DRI is (I know it is direct rendering) and I can't figure out how to enable it. FYI I'm trying to run a couple of games on wine.

---

### Post by dcstar on 2009-02-14
> **graemejager said:**
> Alright, I've been looking around and I don't understand what DRI is (I know it is direct rendering) and I can't figure out how to enable it. FYI I'm trying to run a couple of games on wine.

It is the "3D" features that your video hardware *might* support - but it depends on the drivers available.

Enter this command to verify if it is available to you:

```
glxinfo | grep direct
```

---

### Post by graemejager on 2009-02-14
I got 

direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

---

### Post by dcstar on 2009-02-14
> **graemejager said:**
> I got 

direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

Then you need either video hardware that supports DRI under Linux, or a driver that enables it.

---

