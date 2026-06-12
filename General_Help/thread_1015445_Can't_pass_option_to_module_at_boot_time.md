---
title: "Can't pass option to module at boot time"
date: 2008-12-18
forum: General Help
---

### Post by carrerag on 2008-12-18
Hello everyone,

I have a network card that I need to disable checksum offloading.  After much digging I found that I could pass an option to the module when it loads.  For example the following works:

"rmmod 3c59x" and then "modprobe 3c59x hw_checksums=0"

So I created a file in modprobe.d "3c59x" with the following line:

options 3c59x hw_checksums=0

But it doesn't work at boot time.  I can later remove the module and reinstall and it DOES read that file and work.  So... what am I missing to pass this parameter at the initial boot?  Do I need to make this change in some other configuration file?

Thanks,
Glen

---

