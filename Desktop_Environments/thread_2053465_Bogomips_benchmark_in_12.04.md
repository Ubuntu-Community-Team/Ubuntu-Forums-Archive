---
title: "Bogomips benchmark in 12.04"
date: 2012-09-05
forum: Desktop Environments
---

### Post by Colonel-Panic on 2012-09-05
Hi all!

Noob here.):P

I was given a request to run bogomips benchmark on a workstation with server board (Supermicro 4-way), and Intel Xeon E5 4xxx series CPU's (2 physical CPU's).

However, when following the instructions from Linus I get error:

root@this:/home/this/Desktop/bogo-1.2# make
gcc -DPORTABLE_BOGOMIPS -Wall -O2 -fomit-frame-pointer -finline-functions -N -s -o bogomips bogomips.c
/usr/bin/ld: [COLOR="Red"]cannot find -lgcc_s[/COLOR]
/usr/bin/ld: [COLOR="red"]cannot find -lgcc_s[/COLOR]
collect2: [COLOR="red"]ld returned 1 exit status[/COLOR]
make: *** [COLOR="red"][bogomips] Error 1[/COLOR] 

Is there a way to get past this error that I have failed to find?

Regards,

---

### Post by Colonel-Panic on 2012-09-06
Anyone?

I'd appreciate any pointers really. Anything at all.


Regards,

---

