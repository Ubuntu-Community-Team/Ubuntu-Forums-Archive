---
title: "Nautilus - Segmentation Fault"
date: 2009-05-01
forum: General Help
---

### Post by arepaking on 2009-05-01
Hello experts,

I am using Jaunty 9.04 and Nautilus stopped working for me after connecting/disconnecting a Hard Drive via USB. It doesn't open any folder and I keep getting the same message every time I try to use it.

The messagges are:
```

May  1 15:39:48 Dell kernel: [  649.044955] nautilus[3278]: segfault at 8578000 ip b5c0c7dd sp b5853fc0 error 4 in libbrasero-media.so.0.1.1[b5bfc000+1e000]
May  1 15:40:32 Dell kernel: [  692.868802] nautilus[3509]: segfault at a3a7000 ip b5d877dd sp b59cefc0 error 4 in libbrasero-media.so.0.1.1[b5d77000+1e000]
May  1 15:40:51 Dell kernel: [  711.907935] nautilus[3530]: segfault at 975b000 ip b5d0a7dd sp b5951fc0 error 4 in libbrasero-media.so.0.1.1[b5cfa000+1e000]
```

Does anyone knows if this is a bug? how could I overcome this??

Thanks in advance,
AK

---

### Post by soro2005 on 2009-05-01
Open Synaptic look for brasero and libbrasero-media0 and try whether reinstalling them helps.

And [this is the bug](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/361882) you're looking for.

---

