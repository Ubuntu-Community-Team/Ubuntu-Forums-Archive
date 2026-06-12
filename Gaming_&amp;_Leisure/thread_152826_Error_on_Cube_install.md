---
title: "Error on Cube install"
date: 2006-03-30
forum: Gaming &amp; Leisure
---

### Post by telepathetic on 2006-03-30
Trying to install Cube on Dapper:
sudo sh cube_unix

gives this error:
./bin_unix/linux_client: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

but when i look in synaptic i see that i have this installed:
package: libstdc++6 
installed version: 4.0.3-1ubuntu3
latest version: 4.0.3-1ubuntu3
description: The GNU Standard C++ Library v3

any ideas?  I'm pretty clueless if you hadn't already figured that out.
thanks for the help!
-telepathetic

---

### Post by EviL_Me on 2006-03-31
[QUOTE=telepathetic]Trying to install Cube on Dapper:
sudo sh cube_unix

gives this error:
./bin_unix/linux_client: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

but when i look in synaptic i see that i have this installed:
package: libstdc++6 
installed version: 4.0.3-1ubuntu3
latest version: 4.0.3-1ubuntu3
description: The GNU Standard C++ Library v3

any ideas?  I'm pretty clueless if you hadn't already figured that out.
thanks for the help!
-telepathetic[/QUOTE]

If you do a synaptic search for libstdc++, then do you see more results than libstdc++6 ? When there are install those.

---

### Post by Perfect Storm on 2006-03-31
```
sudo apt-get install libstdc++5
```

---

