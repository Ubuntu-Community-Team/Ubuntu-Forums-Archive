---
title: "Blur on an Intel 945: does it work ?"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by weirdocollector on 2007-10-20
Hi everybody,

I've installed successfully Ubuntu 7.10 on one my two Lenovo 3000 N-100 laptops, which mount an Intel 945GM graphic card.

Practically all Compiz-Fusion effects work OK, with the exception of  BLUR, that when activated just slows down all the graphics to a near halt.

I have Windows Vista installed on my other N-100 and the BLUR effect works perfectly, so that does not seem to be a hardware limitation.

Could some one help me on this subject ?

Is it possible to make BLUR work with my graphic card ?

Thanks in advance for any help.

---

### Post by weirdocollector on 2007-11-05
Sorry to bump this...

Could some good soul help me ?

Thanks again.

---

### Post by floke on 2007-11-06
Have a free bump - I have the same problem
Blur worked perfectly in Edgy with Beryl btw.

---

### Post by LinuxIsInnovation on 2007-12-14
Bump again:
Same problem for me..

---

### Post by klange on 2007-12-14
The Compiz blur plugin uses a stencil mask applied to some textures to create its blurring effects. The driver for the i910 doesn't support this (yet, at least).
The blur plugin in Beryl used GL_CONVOLUTION to create the effect, which is effectively slower on hardware that can handle the stencil mask. There is a plugin that replicates this effect in the works for Compiz. I'm looking forward to it as well.

---

