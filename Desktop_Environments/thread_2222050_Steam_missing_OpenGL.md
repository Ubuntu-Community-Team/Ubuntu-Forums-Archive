---
title: "Steam missing OpenGL?"
date: 2014-05-04
forum: Desktop Environments
---

### Post by bewareofthephog on 2014-05-04
I found a thread on this a while back that solved my issue but can't seem to find it.  I've got an MSI R9 270 and would like to play steam games.  After installing the proprietary drivers from the ATI site I can't seem to install the right package (mesa) without breaking my video card setup because it pulls in nvidia.  From memory I *think* the package I'm looking for is libmesa-headers or something like that?  Sorry for the vague post, I'll provide any information that's needed!  tyia!

---

### Post by bewareofthephog on 2014-05-05
Figured it out (a different way)

I'm now using this script

```

#!/usr/bin/env bash
export LD_LIBRARY_PATH=/usr/lib/i386-linux-gnu:/usr/lib/i386-linux-gnu/dri:/usr/lib/i386-linux-gnu/fglrx:/usr/lib/i386-linux-gnu:gconv

steam

```

---

