---
title: "Sauerbraten and Nexuiz"
date: 2009-02-26
forum: Gaming &amp; Leisure
---

### Post by AugustHovel on 2009-02-26
Hi,

I have the same problem with Nexuiz and Sauerbraten. I load up these games, and I get a black screen. I DO hear sound, however.

I'm running Ubuntu 8.10 32-bit.
Processor is AMD 64 X2 5200+
4 Gig Ram
NVIDIA GeForce 6150se + nForce 430 chipset
My Current resolution is 1600x1200, 24-bit
I'm running NVIDIA accelerated graphics card driver version 177 (as recommended by the Ubuntu software)

Any ideas?

---

### Post by Bölvaður on 2009-02-26
what about other games that require opengl.. do you still have black screen if you turn compiz off? (System &#8594; Preferences &#8594; Appearance ; visual effects &#8594; none)

---

### Post by AugustHovel on 2009-02-27
> **Bölvaður said:**
> what about other games that require opengl.. do you still have black screen if you turn compiz off? (System &#8594; Preferences &#8594; Appearance ; visual effects &#8594; none)

I don't use compiz. I ran the gears (for some reason the name of the command escapes me) test, and it works. I can run Guild Wars windowed but not fullscreen, but I'm not sure if that's dependant on OpenGL.

I appreciate any help I can get on this.


Thanks

---

### Post by MarblePanther on 2009-02-27
> **AugustHovel said:**
> I don't use compiz. I ran the gears (for some reason the name of the command escapes me) test, and it works. I can run Guild Wars windowed but not fullscreen, but I'm not sure if that's dependant on OpenGL.

I appreciate any help I can get on this.


Thanks

glxgears is the command just for future reference

---

### Post by AugustHovel on 2009-03-02
I got it to work -- I was using NVidia Driver version 177. I downgraded to version 96, and now everything seems to be working fine. *shrug*

Oh well.

---

