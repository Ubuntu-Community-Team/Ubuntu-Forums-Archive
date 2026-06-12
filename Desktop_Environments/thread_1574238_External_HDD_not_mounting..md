---
title: "External HDD not mounting."
date: 2010-09-14
forum: Desktop Environments
---

### Post by peter_parker on 2010-09-14
Hey guys,

i have Ubuntu 10.4 installed.  i have a external hdd that is formated as HFS+.

When i connect it, nothing happens in ubuntu but the hdd lights up at least..

am i missing something?

Thanks

---

### Post by Azyx on 2010-09-14
> **peter_parker said:**
> Hey guys,

i have Ubuntu 10.4 installed.  i have a external hdd that is formated as HFS+.

When i connect it, nothing happens in ubuntu but the hdd lights up at least..

am i missing something?

Thanks

You need to install HFS+ support. Go to System-->Adminstartion-->Synaptic and search for hfs

The package is hfsplus and hfsutils. 

/cheers

---

### Post by peter_parker on 2010-09-14
Thanks!  I'll try it when I get home tonight.

---

### Post by peter_parker on 2010-09-14
Thanks Azyx!  got it to work after i installed and command:  sudo mount -t hfsplus /dev/sdc /home/<username>/Desktop/External_HDD

---

