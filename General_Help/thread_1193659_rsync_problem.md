---
title: "rsync problem"
date: 2009-06-21
forum: General Help
---

### Post by canter690 on 2009-06-21
Am having a problem with rsync.  Have 4 Dlink NAS devices connected to the network. Config is as follows
device1 name - A_S_MASTER
device2 name - A_S_SECONDARY
device3 name - T_Z_MASTER
device4 name - T_Z_SECONDARY

As the names suggest the secondary device is my backup device.

All mounted via fstab.

using rsync -avP device1/share device2/share works fine

when I do a rsync -avP device3/share device4/share in another window it appears to work but in fact nothing is being copied - the files are being read but not written.

rsync -avniP device3/share device4/share works fine - output as expected

using grsync however does work
using cp also works

Am running 64 bit Jaunty


Any suggestions on how to debug this, or if this is just a bug ?

---

### Post by sedawk on 2009-06-21
Does rsync show the directories when asked to list files instead of syncing:
```

rsync device3/share/
rsync device4/share/

```

(I have one server+directory where this freezes!)

Another test would be to try it on subdirectories for debugging, e.g.:
```

rsync -avP device3/share/music/ device4/share/music/

```

---

### Post by canter690 on 2009-06-21
thanks for the suggestions but not shedding any light

suggestion 1
rsync shows the directories as expected

suggestion 2
same problem with sub directories

---

