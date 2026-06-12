---
title: "Xgl crashes"
date: 2006-07-31
forum: Desktop Environments
---

### Post by zerwas on 2006-07-31
***_[COLOR="Red"]SOLVED[/COLOR]_***


Hello,

First sorry for the not good topic-name but i don't know what i should better write.

I have the problem that - when i start compiz (or do anything that has to do with OpenGL e.g. glxgears) - my Xgl-server crashes and gives me this error message:
```
X error of failed request: GLXUnsupportedPrivateRequest
```
When i tried an older Nvidia-driver (8756) i got the same error message :(
I think i should mention, that i had to symlink the libGL.so.1 to my MESA-libGL, because the nvidia-driver would else have overwritten it. Many other had this problem and solved it this way (else i got 

Perhaps anybody here can help me out of this. I know that i had XGL/Compiz working many weeks ago in my old dapper-installation.
Google couldn't help me.

Specs:
Distribution: Ubuntu Dapper 6.06
GPU: Geforce 6600
arch: i386
compiz: quinnstorm (compiz 0.0.13-quinn26)
Loaded plugins: don't know
You can see my current xorg.conf here: [xorg.conf]("http://rafb.net/paste/results/QjRWjU80.html")

---

### Post by jasutton on 2006-07-31
I would try getting OpenGL apps (like glxgears) working in X without all the Xgl/Compiz stuff first.  Those extra things seem to give strange errors for sometimes simple problems. :)

Also, about the Mesa-libGL thing, I think I ended up having to download the libMesa package from quinn's repos and extracting it's version of libGL to a specific location to get something to work but I don't remember exactly.

Hope that helps. :)

---

### Post by zerwas on 2006-08-01
Thank you very much for responding jasutton. :)
I solved the problem yesterday night.
[solution]("http://www.compiz.net/viewtopic.php?pid=18655")

---

