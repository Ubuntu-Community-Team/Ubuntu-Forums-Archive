---
title: "Dell GX-110 Magic GRUB (or something else_ Configuration?"
date: 2010-08-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MikeRivers on 2010-08-16
I have Ubuntu Studio 10.04 installed on this old Dell GX-110 and I'm getting the dreaded and apparently fairly common messages on bootup:

error: no suitable mode found
error: unknown command 'terminal'

It boots and runs OK, it's just that this is kind of annoying. 

Web research takes me to several possible solutions that don't work here. Consensus is that it has to do with the monitor resolution setting in the grup.cfg file. (I guess that means it's running grub2)  In my file, the VGA=640x480 line is commented out. I tried removing the # and rebuilding grub.cfg, and that didn't work. I'm not sure what resolutions are offered by the motherboard graphics controller so I'd rather not just start poking in resolutions at random hoping to find something that works when I'm not even sure this is a good trail to follow. 

One suggestion was to run the command hwinfo --framebuffer to get a list of resolutions but that gives me nothing. (suspicious???) hwinfo --gfxcard doesn't tell me anything about resolution, but does say Primary display adapter: #10. Does that mean anything useful? 

If I hold the Shift key while it's booting to get the "secret" boot menu and select "Ubuntu, with Linux 2-6.32-21-generic (the first item in the menu) it boots without the error messages.

The magic solution, anyone?

---

