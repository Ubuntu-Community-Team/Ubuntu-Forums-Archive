---
title: "Cannot fix my screen resolution again"
date: 2009-06-02
forum: General Help
---

### Post by gamesnepal on 2009-06-02
I previously had a [_[COLOR="Blue"]simple screen resolution problem which I fixed here[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=5812065").

But I have this problem again after upgrading to 9.04. I cannot increase my screen resolution more than 800x600. I try to view the Hardware Drivers like the last time and I get nothing :

[IMG]http://img190.imageshack.us/img190/5006/screenshot1r.png[/IMG]

I cannot find the NVIDIA accelerated graphics driver in the proprietary drivers list :(

How to I increase my screen resoluion ?

Thanks

---

### Post by MichaelSammels on 2009-06-02
Try this:

```
sudo apt-get install nvidia-settings
```

---

### Post by gamesnepal on 2009-06-03
I did that and still I get nothing.

Edit: I updated my system and the nokia drivers appeared in my hardware settings and I could fix the screen resolution problem. Thanks for the support.

---

