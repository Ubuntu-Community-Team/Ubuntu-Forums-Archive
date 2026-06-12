---
title: "limewire has god powers."
date: 2005-12-08
forum: Desktop Environments
---

### Post by fourchannel on 2005-12-08
i have a dedicated tower set up running limewire. on system boot, gdm automatically logs user limewire in, and in .xsessions launches openbox, few apps, then limewire. more specifically, it launches this.

```
/home/limewire/LimeWire/runLime.sh&
``` 
but it gives limewire root privileges, and I don't want that.

```
$ls -Flh ~/LimeWire/runLime.sh
-rwsr-xr-x  1 limewire limewire 3.0K 2005-10-25 13:28 /home/limewire/LimeWire/runLime.sh
``` 
i set the SETUID bit and changed ownership to limewire:limewire for the entire LimeWire/ directory.

but I can do this.

```
$su
$echo 'test' > testfile.mp3
$chown root:root testfile.mp3
$chmod 755 testfile.mp3
``` 
go into limewire, find the test mp3, and delete it. and when i check, it really deletes it, not just 'hides' it.

which isn't supposed to happen.

any suggestions?

---

