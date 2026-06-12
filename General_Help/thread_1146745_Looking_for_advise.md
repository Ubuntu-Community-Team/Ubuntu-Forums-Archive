---
title: "Looking for advise"
date: 2009-05-02
forum: General Help
---

### Post by Pulsewave on 2009-05-02
Hello Friends.
.
I timed my 9.04 boot without modifications at 25 seconds.
.
I made two tweaks in the hopes of making things faster.
.
1. Changed BIOS to use AHCI 
2. Installed "preload"
.
Boot has slowed down to 30 seconds after these changes. 
.
Anyone have any ideas on what has cause the extra 5 seconds to be added to the boot time ?

Thanks In Advance

---

### Post by Brandon Williams on 2009-05-03
The package description for preload says "Note that installing preload will not make your system boot faster". What gave you the impression that it will help your boot time? I'm not saying that it won't, I just can't find an indication that it will.

Did you reinstall after enabling AHCI? I see indications in various places that you should set this to what you want before installation, and that it can cause problems if you change it after the fact. I've only seen general reference to this -- nothing specific to Ubuntu -- so I can't be sure that this would have anything to do with the slow down. However, given the fact that the preload package says that it won't help with boot time, my guess would be that switching to AHCI is behind the slower boot time.

This is just my best guess, though, since I don't have direct experience with this problem.

---

