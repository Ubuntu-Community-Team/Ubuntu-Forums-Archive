---
title: "Coin error running FreeCAD"
date: 2010-03-07
forum: Education &amp; Science
---

### Post by swiftwood on 2010-03-07
Hello,

I downloaded and built FreeCAD 
freecad_0.9.2646.5-1_i386.deb

and Pivy
pivy_0.5.0~svn765.orig.tar

It comes up, but I get the following error when I go to open a new file:


> Coin error in SoNode::GLRenderS(): GL error: 'GL_INVALID_ENUM', nodetype: Separator (set envvar COIN_GLERROR_DEBUGGING=1 and re-run to get more information)
Illegal storage access...


thoughts?

---

### Post by not_a_phd on 2010-03-08
First thought that comes to me is that freeCad is alpha software, and not ready for the end user. (A quote from their website.) If you are signing up to assist them in testing, I would recommend you try to open a very simple file that you generate (either within freeCad, or a simple line drawing from qCad). This might help narrow down if the issue is within some complex rendering being done in the app, or just a function of the application opening...

---

### Post by swiftwood on 2010-03-11
unfortunately it's simpler than that

I just try to great a new file, and it blows up.

---

### Post by drewm1980 on 2010-06-01
> **swiftwood said:**
> unfortunately it's simpler than that

I just try to great a new file, and it blows up.

Same on Debian.  Install from apt, new file, crash.  "Illegal storage access..."

I'm really looking forward to this software when it is ready; here's hoping they achieve their development goals!

---

### Post by 23dornot23d on 2010-06-01
Just loaded into the latest version of Mint and it seems to be working ok
was working on the BOP in wings3d ... so put this file in as a OBJ file ....

[IMG]http://img109.imageshack.us/img109/2905/oneclamp388a.jpg[/IMG]

---

