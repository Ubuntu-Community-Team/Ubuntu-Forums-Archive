---
title: "constantly crashing"
date: 2008-12-19
forum: General Help
---

### Post by Coruba67 on 2008-12-19
hi guys,

have recently put together a ubuntu box at home to run myth, problem is that it seems to crash fairly often and am not sure why... 

Dec 20 12:32:36 Osiris kernel: [  442.809542] Bulk In Failed. Status=-71, BIIdx=0x1, BIRIdx=0x1, actual_length= 0x0
Dec 20 12:33:21 Osiris kernel: [  488.428532] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 521

it got this from var/log/messages wondering if its a clue? where else can i look?

---

### Post by cariboo on 2008-12-20
You problem seems to cause by a bug in the kernel, I would suggest using a different kernel. if that is possible.

You didn't mention what version you are using, so it is pretty hard to suggest which kernel to use.

Jim

---

