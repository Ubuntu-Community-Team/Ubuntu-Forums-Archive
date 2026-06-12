---
title: "Ubuntu 6.06 and compiz/XGL on i810"
date: 2006-06-14
forum: Desktop Environments
---

### Post by pop killer on 2006-06-14
Hi

i've successfully installed XGL and compiz, and works.

dri is enabled on X startup (i've see logs)
but glxinfo | grep direct say that dri is not enabled...

the scrolling with mouse whell is slow, is slow the resizing of the windows too, and pc reply on keyboard pressing is slow...

i think it's for dri, can you help me?


sorry for my bad bad bad english :-(

---

### Post by halfvolle melk on 2006-06-14
> Composite Extension

If you've enabled trasparency, and you've added the Composite extension to the xorg.conf file, the ATI driver will disable DRI.
The only way to use 3D and the ATI OpenGL drivers is commenting the Option "Composite" "Enable" line.
The composite extension is still considered "experimental" by the X.org organization and ATI has stated they will not support features that are classified as such.
from [http://wiki.cchtml.com/index.php/Frequently_Asked_Questions](http://wiki.cchtml.com/index.php/Frequently_Asked_Questions)
So that's a bummer for those of us with an ATi. I could be wrong but I don't think you can have both.

---

### Post by hezral on 2006-06-14
i think he is using the intel i810.. not ATI...

---

### Post by pop killer on 2006-06-14
yes

---

### Post by halfvolle melk on 2006-06-14
Oops, sorry about that. I misread your post.

---

