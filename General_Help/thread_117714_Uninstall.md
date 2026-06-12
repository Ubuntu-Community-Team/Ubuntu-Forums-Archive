---
title: "Uninstall?"
date: 2006-01-15
forum: General Help
---

### Post by abrovink on 2006-01-15
I have this file:
doom3-linux-1.1.1286-demo.x86.run

and to install it i just ```
sudo ./doom3-linux-1.1.1286-demo.x86.run
```

but how do i uninstall the game?

Is there some better way to install this file using ```
dkpg
``` or something? :confused:

---

### Post by abrovink on 2006-01-17
:confused:

---

### Post by lamego on 2006-01-17
When you have run 
  ./doom3-linux-1.1.1286-demo.x86.run
It probably presented you yhe list with the path of the files being installed.
They should have been installed into their own path so you just need to remove them with rm dir .
There maybe some other things installed like a menu entry or a launcher script, you will need to remove those manually also.

If you use an installer which does not provide an "uninstall" function you can't do much better than this.

---

