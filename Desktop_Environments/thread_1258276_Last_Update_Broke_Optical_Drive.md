---
title: "Last Update Broke Optical Drive"
date: 2009-09-04
forum: Desktop Environments
---

### Post by zoey_s on 2009-09-04
I am running Jaunty Jackalope and after the last update the OS can't see the optical drive. I checked to see if the sg module was running and I got this message; FATAL:module sg not found.

I checked to make sure that the motherboard could see the optical drive by booting to a live cd and it worked just fine, so the motherboard sees it.

I also tried;
find /lib -iname "*sg*"
/lib/brltty/libbrlttysgs.so
/lib/modules/2.6.28-15-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.28-15-generic/kernel/net/decnet/netfilter/dn_rtmsg.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/media/video/videobuf-dma-sg.ko
/lib/modules/2.6.28-15-generic/kernel/drivers/char/ipmi/ipmi_msghandler.ko
/lib/modules/2.6.28-11-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.28-11-generic/kernel/net/decnet/netfilter/dn_rtmsg.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/media/video/videobuf-dma-sg.ko
/lib/modules/2.6.28-11-generic/kernel/drivers/char/ipmi/ipmi_msghandler.ko
/lib/modules/2.6.28-14-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.28-14-generic/kernel/net/decnet/netfilter/dn_rtmsg.ko
/lib/modules/2.6.28-14-generic/kernel/drivers/media/video/videobuf-dma-sg.ko
/lib/modules/2.6.28-14-generic/kernel/drivers/char/ipmi/ipmi_msghandler.ko
/lib/modules/2.6.28-13-generic/kernel/sound/isa/snd-sgalaxy.ko
/lib/modules/2.6.28-13-generic/kernel/net/decnet/netfilter/dn_rtmsg.ko
/lib/modules/2.6.28-13-generic/kernel/drivers/media/video/videobuf-dma-sg.ko
/lib/modules/2.6.28-13-generic/kernel/drivers/char/ipmi/ipmi_msghandler.ko

I tried booting into the old kernel and that didn't help either.

I haven't a clue as to how to fix the problem.

zoey

---

