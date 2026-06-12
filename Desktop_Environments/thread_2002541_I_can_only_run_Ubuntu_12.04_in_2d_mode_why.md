---
title: "I can only run Ubuntu 12.04 in 2d mode why?"
date: 2012-06-12
forum: Desktop Environments
---

### Post by rookie2linux on 2012-06-12
I am pretty new to this ubuntu  and had to spend 2 days upgrading from 8.04 to 12.04 but I got it done . And it wont run in 3d mode?? It says compiz failed to run. it starts to work a little but I don't get Unity . But in 2d mode it lights right up no problems at all. Is there something that can be done? I appreciate the assistance and patience :)
Dom

---

### Post by 3Miro on 2012-06-12
This usually indicates problems with the video cards. Compared to 8.04, proprietary driver support was dropped form some old ATI cards and Unity 3D requires more effects so old Nvidia cards may not run with Unity either. Many machines that could run compiz in 8.04 will not be able to run Unity 3D.

What is your video card and what driver are you using?

---

### Post by rookie2linux on 2012-06-12
I'm using an onboard nvida 5150LE 256mb but I have 2gb of ram

---

### Post by 3Miro on 2012-06-12
You RAM is certainly enough, but your video card is too old for Unity 3D. You can keep using Unity 2D if you like it, you should also consider using a different DE.

LXDE and XFCE are very light and fast and I think both will work better on your hardware. KDE is heavy, but it may work better than Unity. Then you have the Gnome 2 ports of MATE and Cinnamon.

Here is a good page that tells you how to install other desktop environments:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by rookie2linux on 2012-06-14
> **3Miro said:**
> You RAM is certainly enough, but your video card is too old for Unity 3D. You can keep using Unity 2D if you like it, you should also consider using a different DE.

LXDE and XFCE are very light and fast and I think both will work better on your hardware. KDE is heavy, but it may work better than Unity. Then you have the Gnome 2 ports of MATE and Cinnamon.

Here is a good page that tells you how to install other desktop environments:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Thanks for the helpful link..:guitar:
But this is what I ended up doing I went got some cd's and burnt a 12.04 64bit copy and did a fresh install. and updated . But this time it let me install the nvida driver that it would not let me b4 . So now I have it in 3d mode. I appreciate all the help that  I've gotten and I'm sure I'll need more b/c  I'm hooked on Ubuntu/Linux no more  windows for me.
Dom

---

