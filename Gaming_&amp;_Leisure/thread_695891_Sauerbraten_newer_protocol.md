---
title: "Sauerbraten newer protocol"
date: 2008-02-13
forum: Gaming &amp; Leisure
---

### Post by 1467 on 2008-02-13
all but 2 of the multiplayer servers say newer protocol y 
and how do you fix it? is that what the patch is for but i cant install the patch when i enter ./configure i get   "./configure: No such file or directory"

---

### Post by FrozenFox on 2008-02-13
That probably means that you are using an old version of sauerbraten.

If you get an error trying to use the patch saying there is no configure, that means you are in the wrong folder in the terminal 95% of the time.

However, I won't bother trying to help you do it that way when there's an easy way to do it:

[http://mirror.ne.gov/debian/pool/contrib/s/sauerbraten/sauerbraten_0.0.20071227.dfsg-1_i386.deb](http://mirror.ne.gov/debian/pool/contrib/s/sauerbraten/sauerbraten_0.0.20071227.dfsg-1_i386.deb)
 
Try downloading this file and double clicking it. It will hopefully let you install the newest version of sauerbraten and do it for you. It works great for me on Hardy.

---

### Post by 1467 on 2008-02-13
ok it says "error : Dependency is not satisfiable:libc6"
so i did sudo aptitude install libc6 but i still got error : Dependency is not satisfiable:libc6

---

### Post by Perfect Storm on 2008-02-13
Here's a guide how you can compile it: [http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten](http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten)

---

