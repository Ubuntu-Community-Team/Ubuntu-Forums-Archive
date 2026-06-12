---
title: "open office 2 - IMPRESS crashes"
date: 2005-10-09
forum: Desktop Environments
---

### Post by iakudi on 2005-10-09
I have just upgraded to Breezy and am trying to use openoffice impress to open up a PowerPoint presentation. In the previous version (Hoary 5.04) I had no problems opening these slides and even managed to install JRE to see some of the animation.

Since I got to Breezy, I find that if I try to open these same slides, they open easily but then just freeze causing all my openoffice applications to crash (I lost half an essay - thankfully recovered). The other apps like Writer etc. work fine.

Can anyone help please? I am re-installing Impress and will give it another try in the meantime.

---

### Post by fillmore on 2005-12-14
I have the same problem with impress.
The thing I find most annoying is that when impress crashes it manages to crash writer and calc as well.

---

### Post by lx73 on 2005-12-14
I just had that happen, too. I save my .odp as a .ppt and from there it worked. I wonder if this is fixed in OO2.0 (I'm using Ubuntu 5.10's OO1.9.129).

---

### Post by rajaiskandarshah on 2005-12-16
oo.o1.9.129 is buggy. will crash in ubuntu as well as in win xp. oo.o2.0 fixes it and i have installed in my win partition - meaning that i now have to boot to win to use oo.o2.0 which i think is plain silly. i am downloading oo.o2.0 for linux now. but i wished they had it in the ubuntu repositories.

---

### Post by geoybest on 2006-01-06
After a long search in OpenOffice forum, I found a workaround for the Impress freezing problem:
Start OO.o Impress from console like this:
```

export MALLOC_CHECK_=2
/usr/lib/openoffice2/program/soffice

```
I'm using Ubuntu Breezy. It works for me and ppt/odp loads even smoother than ever. But note that after export MALLOC_CHECK_=2, please do "export MALLOC_CHECK_=0" before you use gnuplot, or gunuplot will crash.

---

### Post by _MiniMe_ on 2006-01-09
I have the same problem with OO. I'm using 2.0.1 now with Breezy and it still crashes after opening a .ppt file. And not just OO freezes but the whole desktop. I always have to restart the X-server!! I'm using the same version of OO with WinXP and it works without a problem. I found something interesting in the OO-forum:

[http://www.oooforum.org/forum/viewtopic.phtml?t=28536](http://www.oooforum.org/forum/viewtopic.phtml?t=28536)

The problem seems to come from compiling OO with gcc 4. I don't know if that is true, but it's a fact that the same version that works in Win doesn't work in Ubuntu.

@geoybest: thx! that helped.

---

