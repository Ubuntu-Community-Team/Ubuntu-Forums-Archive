---
title: "Desktop permissions for winbind authenticated users"
date: 2012-04-27
forum: Desktop Environments
---

### Post by r3dl0c on 2012-04-27
After I upgraded to 12.04, anything(xfdesktop, Thunar, nautilus, compiz) that requires access to the root window will not run for a user that authenticated through winbind.  Local machine users appear to work fine.  other programs that pop up their own window appear to be fine.  Any ideas?

---

### Post by dmatthes on 2012-05-08
Hello everybody,

I have the same problem with ubuntu. Can somebody give help?

---

### Post by dmatthes on 2012-05-11
I've solved this problem and everything works fine now. There was a problem with the gvfs-daemon, gvfs-daemons:i386 was installed instead of gvfs-daemons. After executing 'sudo apt-get install gvfs-daemons' the :i386 was removed and no more login problem exists.

---

