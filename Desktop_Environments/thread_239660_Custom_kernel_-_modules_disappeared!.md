---
title: "Custom kernel - modules disappeared!"
date: 2006-08-19
forum: Desktop Environments
---

### Post by philipacamaniac on 2006-08-19
I compiled a custom kernel a while back, using the default Ubuntu config from the 686 kernel, then patching in a bit of code to make my motherboard AGP work.

It was working great for a while, then yesterday I tried to boot and during the boot process I got a whole bunch of "module not found" errors during the hardware detection phase.

It still booted and got me to a desktop. I looked in /lib/modules/ and looked in the directory of my custom kernel. All the modules were gone! There was a symbolic link to my /usr/src directory for this kernel, and a few other things, but no modules!

Where did my modules go? I know I didn't delete them. How could this have happened?

---

### Post by philipacamaniac on 2006-08-20
I still have no idea how this happened, but I did remember that I kept the deb package of the kernel I had compiled. Reinstalled it, and all was well.

Word to the wise: for those really long compile jobs, hang on to that debian package once you've finished compiling.

---

