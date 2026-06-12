---
title: "AIGLX and ATI fglrx version mismatch drama"
date: 2006-07-02
forum: Desktop Environments
---

### Post by soulglo83 on 2006-07-02
Following the install guide located at the root of this thread ([http://ubuntuforums.org/showthread.php?p=1205640&posted=1#post1205640](http://ubuntuforums.org/showthread.php?p=1205640&posted=1#post1205640))
i have been able to install all the compiz and aiglx dependancies and get xorg.conf configured so that i have aiglx composite extension, etc, loading and still have dri.  however, upon launching xorg-air or whatever it is called, from the gdm.conf-custom, xorg tries to load 3 times and spits me back out at a prompt.  Someone from the thread referenced at the beginning of this post, has identical behavior, he and i can both load x fine and even have dri, assuming we do not try and load aiglx, in that even it crashes!  My Xorg.0.log is attatched, but the stanza i find troubling is as follows:

(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg-air/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.25.18
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
[R200Setup] X version mismatch - detected X.org 7.1.0.0, required X.org 7.0.-1.8
(II) UnloadModule: "fglrx"
(II) Unloading /usr/lib/xorg-air/modules/drivers/fglrx_drv.so
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)

and let me apologize for starting a new thread, i know this is troubling for those that this will not help, but i figured this error cannot be isolated, it has occured on 3 seperate installs, and two different machines both with the same video card.

---

### Post by art on 2006-07-02
As far as I know AIGLX does not work with fglrx, you have to use the open source driver ati. If you wanna use fglrx you have to use XGL. Any reason you want AIGLX? In my experience XGL is much better...

---

### Post by soulglo83 on 2006-07-02
dag, figures.  i thought xgl to be too slow, and it cripples opengl apps.  supposedly aiglx would allow only slightly hindered opengl access to apps.  im interested to see if the ati drivers will allow my better overall performance than xgl. well thanks much for the reply art!

---

