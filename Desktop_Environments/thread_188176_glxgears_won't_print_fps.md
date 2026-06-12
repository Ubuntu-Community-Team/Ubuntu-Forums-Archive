---
title: "glxgears won't print fps"
date: 2006-06-03
forum: Desktop Environments
---

### Post by mdh on 2006-06-03
Hi,

When I run glxgears, the OpenGL window pops up, the gears spin, but no fps is printed on the console. Is there an option to force glxgears to print fps. It doesn't seem to like -h or --help as an argument and I have no way of knowing why it doesn't print the fps.

---

### Post by dewbian on 2006-06-03
Try

```
glxgears -printfps
```

And yes, it isn't documented.

---

### Post by Ramses de Norre on 2006-06-03
Or the funny one that actually works:```
glxgears -iacknowledgethatthistoolisnotabenchmark

```

---

### Post by mdh on 2006-06-03
Thanks guys.

The second one is funny ;)

---

### Post by Rackerz on 2006-06-03
You could also try fgl_glxgears just to check everything is working correctly. fgl_glxgears also put's more stress on your card than just 'glxgears'.

---

