---
title: "28-13 kernel causes slow scrolling"
date: 2009-06-21
forum: General Help
---

### Post by GSMX on 2009-06-21
Today, I updated jaunty to the 2.6.28-13-generic kernel (x86_64), but after the reboot, scrolling in firefox / synaptic / nautilus went crazy, every scroll of the mouse button causes the window to completely redraw, at a very slow framerate. It is very annoying and I'm back at the 28-11 kernel, as the new one is unusable.

Anybody suggestions / sollutions ??

(btw, also Hal updated, bus doesn't show signs of lag when booted to the old kernel, so I suppose it's not the problem)

---

### Post by Soul-Sing on 2009-06-21
X issue?
```
glxinfo | grep direct
```

---

### Post by GSMX on 2009-06-23
```
user@laptop:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

```

---

### Post by GSMX on 2009-06-23
And when on the 2.6.28-11, output is this:

```
user@laptop:~$ glxinfo | grep direct
direct rendering: Yes
```

---

### Post by Soul-Sing on 2009-06-23
It seems it is not directly X related...

---

### Post by GSMX on 2009-06-23
well, when I read the output "X Error of failed request:  BadRequest (invalid request code or no such operation)" I think there is a problem with X


(for the sake of clarity: my first post after the OP is on the new kernel, the second is with the old one:: the new one gives the problem)

---

### Post by Arup on 2009-06-23
That means your video drivers have not been upgraded for newer kernels, what drivers were you using btw?

---

### Post by GSMX on 2009-06-23
the 9.6 version of the ati driver

---

### Post by Bachstelze on 2009-06-23
You'll probably just need to reinstall your drivers the same way you installed them the first time.

---

### Post by cottfcfan on 2009-06-23
I had the same problem.
You do need to reinstall the proprietary graphics drivers after a kernel update.

---

### Post by GSMX on 2009-06-23
That indeed did the trick, thanks for the help everyone :D:D

---

