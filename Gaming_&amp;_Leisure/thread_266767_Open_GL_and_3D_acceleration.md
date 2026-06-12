---
title: "Open GL and 3D acceleration"
date: 2006-09-27
forum: Gaming &amp; Leisure
---

### Post by tjjohnso on 2006-09-27
in cedega when it does the tests for open GL and 3D acceleration, my computer fails. and i dont know why.

i have 1.83 GHZ dual core intel
NVidia GEForce GO 7400
and 1 GB of RAM

i have no idea what to do or where to start to get it working.so hope

also. i would like to get compiz working, with wobbly windows and the cube. dont know where to start on that either.

so hopelessly lost. V____V

so i guess what im asking is how to get my Open GL, 3D Acceleration and compiz working

---

### Post by Ziox on 2006-09-27
check to see if direct rendering is working:

```
glxinfo | grep direct
```

---

