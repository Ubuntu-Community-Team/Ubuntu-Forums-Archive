---
title: "X server crash"
date: 2008-01-03
forum: Desktop Environments
---

### Post by dangustaf on 2008-01-03
Hi,

I have enabled 3D support on a virtual machine in VMware Player on my ATI X1600 powered laptop. I'm using the latest ATI drivers 7.12 installed with Envy. Running the virtual machine makes X restart after the following error:

> Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c9581]
1: [0xffffe420]
2: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c45e62]
3: /usr/lib/xorg/modules/extensions//libglx.so(DoCreateContext+0x10e) [0xb7c0ea6e]
4: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c0ec14]
5: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c10b2c]
6: /usr/bin/X [0x815754e]
7: /usr/bin/X(Dispatch+0x1aa) [0x808f47a]
8: /usr/bin/X(main+0x495) [0x8076f05]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d8b050]
10: /usr/bin/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting

If I disable 3D support everything works without restarts. What might be the cause? Is this an X issue or ATI driver issue?

Regards,
Dan

---

