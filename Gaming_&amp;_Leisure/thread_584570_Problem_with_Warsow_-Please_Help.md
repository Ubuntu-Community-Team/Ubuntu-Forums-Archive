---
title: "Problem with Warsow -Please Help"
date: 2007-10-21
forum: Gaming &amp; Leisure
---

### Post by Espreon on 2007-10-21
I tried to start Warsow, but it gave me an error message saying that my OpenGL installation does not support direct rendering and that I would have to install the propietary driver (which I di have fglrx installed).

I am using an ATI Radeon x1400 with the fglrx driver and with XGL, with Compiz-Fusion active.

---

### Post by Hal.9000 on 2007-10-21
Post the output of```
glxinfo | grep 'direct rendering'
```

---

### Post by SupWiz17 on 2007-10-21
> **Hal.9000 said:**
> Post the output of```
glxinfo | grep 'direct rendering'
```
I am having the same problem and I am getting 

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


as a response.

Thanks.

---

### Post by Espreon on 2007-10-23
Sorry I have not replied in so long:

```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".

```

---

### Post by The Pinny Parlour on 2007-11-14
I'm getting this error upon starting Warsow, any ideas on what to do to correct it?

Youre OpenGL installation doesn't support direct
rendering. If you have an NVIDIA or an ATI card you'll probably need to
install the propritary driver.

Thanks

---

### Post by Espreon on 2007-11-27
I am using the proprietary drive...

---

### Post by The Pinny Parlour on 2008-01-01
Bump

---

### Post by The Pinny Parlour on 2008-01-18
Bump

---

### Post by smartalecks on 2008-01-19
do you have the package libxxf86misc1 installed?

---

### Post by The Pinny Parlour on 2008-02-28
> **smartalecks said:**
> do you have the package libxxf86misc1 installed?

Yes I do.  

Thank you for assisting.  I have almost given up on this.  Gaming just sucks a55 on Linux period.  I'm very disappointed that no one has been able to help me with a solution.

---

### Post by The Pinny Parlour on 2008-03-28
Bump

I'm getting this error upon starting Warsow, any ideas on what to do to correct it?

Youre OpenGL installation doesn't support direct
rendering. If you have an NVIDIA or an ATI card you'll probably need to
install the propritary driver.

Thanks

---

