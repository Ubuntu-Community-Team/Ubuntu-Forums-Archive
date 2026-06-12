---
title: "xmame and libGL.so problem"
date: 2007-02-25
forum: Gaming &amp; Leisure
---

### Post by matemargo on 2007-02-25
I've just installed xmame from Synaptic, but when I try to run it from the terminal I get this output:

```

GLERROR: cannot access OpenGL library libGL.so
GLERROR: dlerror() returns [libGL.so: cannot open shared object file: No such file or directory]
Use of OpenGL mode disabled
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  22 (XDGAOpenFramebuffer)
  Serial number of failed request:  16
  Current serial number in output stream:  16

```

Should I install something else or modify any configuration file?

---

### Post by matemargo on 2007-02-25
I have just added a symbolic link:

```

sudo ln -s /usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/lib/libGL.so

```

and now the error is different:

```

GLINFO: loaded OpenGL library libGL.so!
GLINFO: loaded GLU    library libGLU.so!
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  22 (XDGAOpenFramebuffer)
  Serial number of failed request:  16
  Current serial number in output stream:  16

```

Any ideas?

---

