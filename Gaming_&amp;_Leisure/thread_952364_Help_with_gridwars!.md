---
title: "Help with gridwars!"
date: 2008-10-19
forum: Gaming &amp; Leisure
---

### Post by luisjorge on 2008-10-19
Hello everyone! I've been trying to run gridwars for a long time, but with no success. I'm running it in Ubuntu intrepid beta, and I always get the same error at start:

gridwars: brw_vtbl.c:98: brw_new_batch: Assertion `!brw->no_batch_wrap' failed. 
Aborted (core dumped)

Then, after half a second, it closes. Is there anything I can do to fix this?

Thanks in advance!

Luis Jorge.

---

### Post by Grishka on 2008-10-21
how did you install it? I'm on Intrepid as well, and I've used a deb from getdeb, here: [http://www.getdeb.net/app/GridWars+2](http://www.getdeb.net/app/GridWars+2). works well for me.

---

### Post by luisjorge on 2008-10-21
Hi! Thanks for the reply. Well, I also installed it using a package from getdeb, and also downloaded a tar package from the homepage, and I wasn't able to run it either.

Is there something I can do?

Thanks!

---

### Post by yeus on 2008-11-20
I am pretty sure this has something to do with your graphics card... are you running an intel graphics card?  such as X3100/965gm or something similar?  Because I have the same problem and with several programs... 

I am running a Dell Vostro 1310 with the graphics card mentioned above.

(blender for example smetimes crushes with the same error)

greetings, tom

---

### Post by yeus on 2008-11-21
> **luisjorge said:**
> Hi! Thanks for the reply. Well, I also installed it using a package from getdeb, and also downloaded a tar package from the homepage, and I wasn't able to run it either.

Is there something I can do?

Thanks!

yes you can try something if your computer is fast enough

open /etc/X11/xorg.conf

and add to the "Device" section the line:
```

Option "DRI" "false"
```

that helps... problems is that you aren't using complete hardware acceleartion anymore so gridwars might run very slow now...

---

