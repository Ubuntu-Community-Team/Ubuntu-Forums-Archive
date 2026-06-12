---
title: "new kernel changes alsa version"
date: 2009-04-09
forum: General Help
---

### Post by matmat07 on 2009-04-09
Each time I install a new kernel, the alsa version goes back to 1.0.18a, but it is still at 1.0.19 in the last one. I need the newer one, because I can't get sound with other versions. Is there anything I can do beside recompiling alsa each time?

---

### Post by Nepherte on 2009-04-09
As far as I know, you have to compile alsa for each new kernel you create.

---

### Post by sdennie on 2009-04-09
Yes, you have to recompile alsa for each new kernel.  However, this process can be automated at kernel installation time.  In the past, when I was using older kernels and compiling alsa by hand, I made a link in /usr/src called alsa that pointed to the alsa driver I wanted to use for the kernel.  Then, I put this script in /etc/kernel/postinst.d (which you will have to create):

```

#!/bin/bash

echo "Building ALSA drivers for $1" >&2
cd /usr/src/alsa
make clean 2>&1 > /dev/null

./configure --with-kernel=/lib/modules/$1/build --with-cards=hda-intel,usb-audio --with-card-options=all 2>&1

make -j3 2>&1 > /dev/null
make install 2>&1 > /dev/null

exit 0

```

That tries to build the alsa drivers for the newly installed kernel.  But, only the hda_intel and usb_audio drivers.  I can't verify that this will work because I haven't used it for a long time.  It's not an exact fix but, it's a good push in the right direction.

---

### Post by matmat07 on 2009-04-10
It works, thanks a lot. That was one of the major bug I had to deal with.

---

