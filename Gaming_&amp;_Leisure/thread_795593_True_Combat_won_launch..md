---
title: "True Combat won launch."
date: 2008-05-15
forum: Gaming &amp; Leisure
---

### Post by aknisely on 2008-05-15
I installed et and it works fine but when I try to run tc it gives me this error 
Sound memory manager started
Sys_LoadDll(/home/alex/.etwolf/tcetest/ui.mp.i386.so)... 
Sys_LoadDll(/home/alex/.etwolf/tcetest/ui.mp.i386.so) failed:
"/home/alex/.etwolf/tcetest/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/tcetest/ui.mp.i386.so)... 
Sys_LoadDll(/usr/local/games/enemy-territory/tcetest/ui.mp.i386.so) failed:
"libstdc++.so.5: cannot open shared object file: No such file or directory"
Sys_LoadDll(ui) failed dlopen() completely!
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: VM_Create on UI failed

Any body know how I can fix this?

---

### Post by Perfect Storm on 2008-05-15
> "libstdc++.so.5: cannot open shared object file: No such file or directory"


Tried?
```
sudo apt-get install libstdc++5
```

---

