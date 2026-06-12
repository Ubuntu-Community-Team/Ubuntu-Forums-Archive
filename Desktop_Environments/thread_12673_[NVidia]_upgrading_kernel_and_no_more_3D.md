---
title: "[NVidia] upgrading kernel and no more 3D"
date: 2005-01-26
forum: Desktop Environments
---

### Post by GLDavid on 2005-01-26
Hello everyone

I have upgraded my Ubuntu x86 with apt-get dist-upgrade and now, my kernel has this version number : 2.6.8.1-4-386. Before, I was under 2.6.8.1-3-386 and my graphic card (GeForce 5700) worked very well with the Nvidia drivers installed by Ubuntu method.
But now, with this new kernel, any 3D applications (exemple games such as Doom3 or Chromium) would launch. I tried to reinstall the Nvidia driver with Ubuntu method but it didn't have any effect.
So, what are my solutions ?

Thank you very much

Have a nice day.

---

### Post by GLDavid on 2005-01-26
Ok, I've solved it : in this case I only had to add permissions to these files : /dev/nvidia0 and /dev/nvidiactl.

Bye bye.

---

