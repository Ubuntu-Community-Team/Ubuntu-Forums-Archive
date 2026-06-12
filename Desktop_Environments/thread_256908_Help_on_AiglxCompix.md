---
title: "Help on Aiglx/Compix"
date: 2006-09-13
forum: Desktop Environments
---

### Post by CalvinChile on 2006-09-13
Hi, 
I installed Aiglx/Compix according to [http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card]("http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card")

Everything looks fine except that the windows there are no borders and everytime I reboot the PC, kate opens the compiz.start script ....?

How can I recover the borders?

Thanks

---

### Post by Rmorris84 on 2006-09-13
Hey, I also had aiglx and compiz, and i had the same problem, i found help in the #ubuntu-xgl chat room, here is what helped me.

```

#!/bin/bash

LD_PRELOAD=/usr/lib/libGL.so.1.2 compiz --strict-binding --indirect-rendering --replace gconf &

cgwd --replace &

```

make that to a script, and put it in your home folder, chmod it, and run it, and hopefully u get ur borders back.. if not im sorry. (but it worked for me)  also u may be tempted to add that script to run on start-up but i was advised not to just incase, and when i did, sometimes when i started up it would freeze, so i just took it out of the startup and added it to a launcher on my top bar, and run it whenever i get booted up. Of course after talking to a few people (and from reading mark's blog) I heard that there is going to be better support for aiglx soon for compiz, so hopefully this all gets worked out... 

Bob

---

