---
title: "[SOLVED] Compiz Fusion goes incredibly slow, then freezes"
date: 2008-01-11
forum: Desktop Effects &amp; Customization
---

### Post by ataxicwolf on 2008-01-11
So after updating all of my nVidia drivers, I seemed to have successfully installed Compiz-Fusion. The problem is that after being enabled, my computer slowed to a crawl (pretty much un-usable), and then it froze completely.
[U][B]
My Specs Are:[/B][/U]

-nVidia GeForce 8600GT
-Dual Core 2.8GHZ Processor
-Ubuntu Feisty Dawn on External Hard Drive
-1 GB of RAM

So I was wondering how to disable compiz-fusion before loading X (otherwise it will freeze) and more importantly, how to fix Compiz-fusion to be usable.

Thanks for your time and help :)

-Stephen

---

### Post by ataxicwolf on 2008-01-11
Update: I've successfully booted into single user mode and reset my settings using the command:

sudo dpkg-reconfigure -phigh xserver-xorg

I am still trying to fix compiz-fusion though, any ideas?

---

### Post by ataxicwolf on 2008-01-11
Solution was to run Compiz-fusion using this:

compiz --replace --indirect-rendering --loose-binding

Apparently this is a problem with Dual Core Processors and Nvidia 8600GT cards.

Heres a link to the article that helped me:

[http://onlinedev.blogspot.com/2007/09/compiz-fusion-slow-on-nvidia.html](http://onlinedev.blogspot.com/2007/09/compiz-fusion-slow-on-nvidia.html)

---

