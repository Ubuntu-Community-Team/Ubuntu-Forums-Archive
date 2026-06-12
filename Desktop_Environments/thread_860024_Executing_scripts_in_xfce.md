---
title: "Executing scripts in xfce"
date: 2008-07-15
forum: Desktop Environments
---

### Post by stolzi on 2008-07-15
Hello,

i hope i am in the right category for my question...

I have installed xubuntu 8.04  and work with xfce the first time. I have a problem executing scripts in xfce. I will explain it with an example, but i dont think that my problem has something to do with the apps.

I wrote a script which first executes lircd with sudo and then executes xine without sudo. Then i made an entry in sudoers file that i dont have to type the pwd.

If i execute the script from command line all works fine. But when i try to execute it by clicking on the file in xfce lircd starts, but when xine starts  i read in syslog, that lircd cant connect to the given device. 
I am very confused about that, because i start exactly the same script, which should do exactly the same... I made nothing wrong, because i tried several times... start per command line... works... kill lircd and xine... start by clicking... cant connect... kill... start per command line... works!

Has someone an idea?

Thanks
Stolzi

---

