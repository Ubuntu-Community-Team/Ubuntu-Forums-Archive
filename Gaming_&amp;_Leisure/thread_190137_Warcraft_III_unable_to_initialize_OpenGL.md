---
title: "Warcraft III unable to initialize OpenGL"
date: 2006-06-05
forum: Gaming &amp; Leisure
---

### Post by npodges on 2006-06-05
When i try to run Warcraft III under wine, with the -opengl tag, i get the error in the title of my post.

does that mean my wine doesnt have opengl support, or do i have something configured wrong?

thanks,
nick

---

### Post by eqisow on 2006-06-06
It might mean you don't have 3D set up correctly on your system. Do other 3D games work?

---

### Post by Iesos on 2006-06-12
I think I have the same problem. I can run Warcraft 3 without the -opengl flag, but with the flag I get the following message (the last end of it, the outprint that differs from witout opengl):

> err:ole:CoCreateInstance apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x55ddef50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x55ddef88,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  29 ()
  Serial number of failed request:  574
  Current serial number in output stream:  574


And weather my grafics is correctly installed or not, I'm not 100% sure. I can run Diablo 2 with some sort of 3D support, and I get the "nVidia sign" when I start up the computer, and that should be enough right?
Running it without opengl, makes Warcraft 3 terribly slow!

Thanks in advance.

---

