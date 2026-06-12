---
title: "just installed 11.04 - non-stop flickering."
date: 2011-06-09
forum: Desktop Environments
---

### Post by pawan98 on 2011-06-09
Before I begin, i'm sorry if I put this in the wrong forum, I wasn't sure. Anyway I have ran 9.10, 10.04, 10.10, then I installed 11.04 from CD today, I logged in, and NON STOP FLICKERING! I mean like, you couldn't even see the bottom and top bars hardly, they kept flickering, I tried to open Mozilla but non stop flickering, trust me its a bloody night mare! I resolved the issue by using UBUNTU CLASSIC (NO EFFECTS), but I still want to fix this, because i'm that sort of person, and I'm wondering why this has happened, it has worked fine in 3 past versions. Weird. My computer is DELL OPTIPLEX SX270, my video/graphics card is intel 82845G graphics controller. Thanks for reading. :(

---

### Post by Joe- on 2011-06-09
I had the same issue with 11.04, it worked on the first boot but then the graphics just didn't work properly after that, i just went back to 10.04. You could check your drivers System>Admin>Hardware Drivers ?

---

### Post by pawan98 on 2011-06-09
No luck.

---

### Post by Joe- on 2011-06-09
Not sure then, i reinstalled Ubuntu 11.04 twice and using Wubi and still had issues with the graphics, go back to 10.10 or 10.04 is the only help i have sorry.

---

### Post by pawan98 on 2011-06-10
bump

---

### Post by pawan98 on 2011-06-11
uhh how do I do this '

                               
        add the x-swat ppa to update the intel driver 
'

---

### Post by pawan98 on 2011-06-11
Could this be the problem?

pawan@pawan:~$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 865G GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  1.3 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no
pawan@pawan:~$ 



So unity on mine isnt supported.... so how can i fix this in some way

---

### Post by Sombir.Sheoran on 2011-06-11
> **pawan98 said:**
> Could this be the problem?

pawan@pawan:~$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 865G GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  1.3 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no
pawan@pawan:~$ 



So unity on mine isnt supported.... so how can i fix this in some way
I too used same and had problems in second restart.
11.04 Really sucks..

Switched back to 10.10. :(

---

### Post by wildmanne39 on 2011-06-12
> **pawan98 said:**
> Could this be the problem?

pawan@pawan:~$ /usr/lib/nux/unity_support_test -p 
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 865G GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  1.3 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no
pawan@pawan:~$ 



So unity on mine isnt supported.... so how can i fix this in some wayHi, your system can not run unity, but you can use synaptic and install unity 2d and use it, it works great.

---

