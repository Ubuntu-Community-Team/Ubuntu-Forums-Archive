---
title: "compiling ieee80211 before to install ipw2200 in kubuntu"
date: 2005-08-08
forum: Desktop Environments
---

### Post by Luigino on 2005-08-08
Hello everyone, 
i've installed Kubuntu 5.04 and now I was trying to install those ipw2200 things...
just needed to install new ieee80211_1.0.3 and when I do make it says:

luigino@BOLLINOMOBILE:~/ieee80211-1.0.3$ make
Checking in /lib/modules/2.6.10-5-386/build/ for ieee80211 components...

grep: /lib/modules/2.6.10-5-386/build//.config: No such file or directory
grep: /lib/modules/2.6.10-5-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.10-5-386/build M=/home/luigino/ieee80211-1.0.3 MODVERDIR=/home/luigino/ieee80211-1.0.3 modules
make[1]: Entering directory `/lib/modules/2.6.10-5-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.10-5-386/build'
make: *** [modules] Error 2
luigino@BOLLINOMOBILE:~/ieee80211-1.0.3$

so I did a ls on that directory and I have nothing in that directory so I tried, as I read somewhere,to copy in the /usr/src the config-2.6.10-386 file and to run make oldconfig but it said:

luigino@BOLLINOMOBILE:/usr/src/linux-2.6.10$ make oldconfig
make: *** No rule to make target `oldconfig'.  Stop.

plus I have installed the linux-headers in: 

luigino@BOLLINOMOBILE:/usr/src/linux-headers-2.6.10-5-386$ 

but looks like there's no difference with that, it still looks at /lib/modules... directory....

so now I'm stuck...do you have any suggest for this?

BTW I did also updated the repository as suggested in ubuntuguide changing the sources.list then I did an apt-get update but still nothing again...

Thanks a lot, and waiting for your reply I thanks you in advance for your help

C-ya 
Luigi

---

### Post by Luigino on 2005-08-10
Ok folks,

I've figured it out by myself just installing the linux-image-686 since I have a Centrino so then I installed also linux-headers-686 which they made the build directory like a symbolic link that wasn't like so with linux-headers-386 with original image...
Now I've figured to find how to make WEP 128bit working out with my wireless ipw2200 since looks like it's bugged so for now I had to deactivate WEP on da router.

If you have suggests for it, tell me :-) 

Thanks to folks
ciao,
Luigi

---

