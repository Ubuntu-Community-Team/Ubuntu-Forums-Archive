---
title: "Opengl/GLX problem"
date: 2005-09-30
forum: Desktop Environments
---

### Post by cwu on 2005-09-30
I'm doing some opengl programming. I had something that worked fine yesterday. This morning I installed some suggested updates and now I get this when I run the binary:
> freeglut (./car): OpenGL GLX extension not supported by display ':0.0'

Any help would be greatly appreciated.

Thanks.

---

### Post by oneybm on 2005-09-30
I probably am the last person that needs to help but I remember from the How To on installing the latest NVIDIA driver that if you make a chane to or update your Kernel you may have to reinstall the driver.  Was that one of the updates you made?

Just a guess

---

### Post by professor_chaos on 2005-09-30
what do you get when you run glxgears?

you may want to reinstall (first deinstall) glx. Then run "sudo nvidia-glx-config enable"

---

### Post by cwu on 2005-10-04
Great, it works now. Thanks for the tip.

---

