---
title: "RealPlayer10GOLD file not found with sudo"
date: 2006-02-11
forum: Desktop Environments
---

### Post by hugeness on 2006-02-11
hello

have read the previous stuff about realplayer10 here, but i have tried the following:
*account*@*account*:~/Desktop$ chmod +x RealPlayer10GOLD.bin
*account*@*account*:~/Desktop$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
*account*@*account*:~/Desktop$ su *account* ./RealPlayer10GOLD.bin
Password:
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
*account*@*account*:~/Desktop$ sudo ./RealPlayer10GOLD.bin
Password:
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
*account*@*account*:~/Desktop$

got it to work this way on fedora core 4 - is there a glitch in my installation?

thanks!

---

