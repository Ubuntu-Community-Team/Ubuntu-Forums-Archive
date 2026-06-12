---
title: "xserver-xgl very slow"
date: 2008-02-06
forum: Desktop Effects &amp; Customization
---

### Post by n-alexander on 2008-02-06
Hi,

1) I run ATI X1300, proprietary driver from AMD. Driver installed and seems to work fine

2) went to Visual Effects, tried, got "Desktop effects could not be enabled"

3) installed xserver-xgl

4) effects work but OMG is it slow. Even moving a window is a pain - didn't use to before XGL

Is it because my video card is slow?

Or because I didn't actually get 3D acceleration set up properly in the first place?

Thanks,
Alex

---

### Post by Agroth on 2008-02-07
Bump on this one, I'm having the exact same problem.
Works excellent without xserver-xgl but then compiz does not work...

Anyone got any ideas?

---

### Post by MongoosC5 on 2008-02-08
another bump. exact same issue for me too.

---

### Post by n-alexander on 2008-02-08
ATI's control center - Catalyst - reports "no ATI driver" while using xserver-xgl.

From which I deduct that xserver-xgl does not use/inhibits ATI driver. Which means it renders effects in SW, which is slow.

So the next place to look into would be xserver-xgl config file to see if it specifies video driver. If I knew where it were.

If it uses generic driver, I could copy ATI settings from /etc/X11/xorg.conf

---

