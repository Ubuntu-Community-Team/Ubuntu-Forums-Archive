---
title: "For those of you having trouble with Tibia [LINUX CLIENT] I have found the answer!"
date: 2009-01-21
forum: General Help
---

### Post by lordpoee on 2009-01-21
Keep in mind this really only works for users of openchrome but a while back I saw several people asking why Tiba wouldn't run and they were open chrome users so i thought I would put this here.

[https://help.ubuntu.com/community/OpenChrome#openChrome%20and%203D](https://help.ubuntu.com/community/OpenChrome#openChrome%20and%203D)

Follow the compile instructions and you'll be on your way.

NOTE:

They left out one step, go into /lib/modules/`uname -r`/kernel/drivers/char/

Where uname is your Linux Header version. and type

sudo mkdir drm

THEN enter back into the working directory linux-core and run

sudo cp *.ko /lib/modules/`uname -r`/kernel/drivers/char/drm/

And all will be well. :)

---

