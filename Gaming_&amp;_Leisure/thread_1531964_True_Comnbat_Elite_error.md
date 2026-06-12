---
title: "True Comnbat Elite error"
date: 2010-07-15
forum: Gaming &amp; Leisure
---

### Post by Simdog1 on 2010-07-15
well after i downloaded Tce and i ran it it seems like its running then it goes back to desktop with this error
Sys_Error: VM_Create on UI failed
any help please?

---

### Post by Simdog1 on 2010-07-15
well here the whole thing starting from sound
------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/family/.etwolf/tcetest/ui.mp.i386.so)... 
Sys_LoadDll(/home/family/.etwolf/tcetest/ui.mp.i386.so) failed:
"/home/family/.etwolf/tcetest/ui.mp.i386.so: cannot open shared object file: No such file or directory"
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

---

### Post by Perfect Storm on 2010-07-15
> "libstdc++.so.5: cannot open shared object file: No such file or directory"

Install libstdc++5 - It's an old obsolete library so it's not part of the repositories anymore. but you can find it here: [http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

---

### Post by Simdog1 on 2010-07-16
alright figured it out i downloaded the ++6 one since no ++5 and had to do some symbolic linking (whatever that is i saw the tce forums)
apt-get install libstdc++6 
ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5 

if the 2nd command doesnt work do sudo then the command

---

### Post by libertin on 2010-08-09
Got exactly the same problem - apart from the fact, that neither linking nor installing libstdc++5 worked...any suggestions? (ET itself works)

---

### Post by Perfect Storm on 2010-08-09
Are you using 64-bit? If so, you need to download libstdc++5 the 32-bit version you can use getlibs to install 32-bit libs on 64-bit system: wget [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb)

---

### Post by Zal0m0n on 2010-09-28
Yes! a working free fps ty! :)

---

