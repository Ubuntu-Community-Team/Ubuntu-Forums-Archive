---
title: "Why does Firefox 3.1 look so weird???"
date: 2008-11-05
forum: Desktop Environments
---

### Post by turbowei on 2008-11-05
Hi.

I have my firefox 3.0.3 looking good in this screenshot.

(Screenshot_01, the one on left)

The font looks very well.

However, I installed firefox 3.1 beta (from ubuntutweak's repository), and on the same page, it looks far worse with the strangely much "thinner" font.

(Screenshot_02, the one on right)

Why do they look so different?? And how do I make the 3.1 firefox look the same as 3.0.3??

Thanks

---

### Post by turbowei on 2008-11-05
Oh by the way, I am using Deja Vu Sans fonts in both screenshots.

And this is for Intrepid.

---

### Post by turbowei on 2008-11-05
After some carefully research (googling), it seems that firefox 3.1 beta (even from repository) is compiled without the native cairo library.

[http://ubuntuforums.org/showthread.php?t=665486](http://ubuntuforums.org/showthread.php?t=665486).

"The reason you have no subpixel hinting is that Fx3 uses the in-tree cairo library, which has no LCD-filtering patches applied. You, or your distro's package maintainer, will have to compile it with following option in .mozconfig: -enable-system-cairo. You'll also need to use this command: export LDFLAGS='-lX11 -lXrender' "

---

### Post by matthewn on 2009-03-09
If I am not mistaken, the following commands solve this problem. This has worked for me on two boxes, one a desktop, one a laptop...

```
sudo mkdir /etc/fonts/conf.disabled
sudo mv /etc/fonts/conf.d/10-* /etc/fonts/conf.disabled
sudo mv /etc/fonts/conf.d/53-* /etc/fonts/conf.disabled
```

I think you have to restart X for this to take effect. More on this at [http://www.mahnamahna.net/blog/tech/fontfix.html](http://www.mahnamahna.net/blog/tech/fontfix.html).

Hope this helps.

---

### Post by WorLord on 2009-05-28
> **matthewn said:**
> If I am not mistaken, the following commands solve this problem. This has worked for me on two boxes, one a desktop, one a laptop...

```
sudo mkdir /etc/fonts/conf.disabled
sudo mv /etc/fonts/conf.d/10-* /etc/fonts/conf.disabled
sudo mv /etc/fonts/conf.d/53-* /etc/fonts/conf.disabled
```

I think you have to restart X for this to take effect. More on this at [http://www.mahnamahna.net/blog/tech/fontfix.html](http://www.mahnamahna.net/blog/tech/fontfix.html).

Hope this helps.

Good lord.  FINALLY FIXED.  At least, for me.  :D

---

### Post by binbash on 2009-05-29
Thanks i will try it out.

---

