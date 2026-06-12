---
title: "Nautilus 3.4.2 on Ubuntu 12.04 LTS Took 1.6 GB of RAM And Became Sluggish"
date: 2014-03-28
forum: Desktop Environments
---

### Post by easygoing on 2014-03-28
I have Ubuntu 12.04 LTS on Lenovo TS130 with 4GB of RAM.
After running continuously for over a week, sometimes with heavy load, the system became very sluggish. Every application took a long time to respond. Firefox browser became much slower in opening a new tab and load a new page. Nautilus file explorer became extremely sluggish. Every operation, even switching to fore ground, will cause a gray-out of the window and take several second to respond. The memory usage is about 80%, and SWAP usage the same level.
Out of frustration, I tried to close applications. I closed Firefox, without much improvement. 3 instances of Nautilus is the only application running in the desktop (I have a web server program and related programs running idle in the background, taking about 40% of RAM). After I closed the 3 Nautilus instances, miracle happened. The RAM usage dropped from 80% to 40%, in 3 stages. SWAP usage did the same. Then the whole system became as fast as before. I tried other applications, and felt that the desktop environment completely recovered.
Needless to say that I am stunned by this happy accident.
Anybody experiencing the same?

---

### Post by ajgreeny on 2014-03-28
Not seen that, but just for your info, rather than closing down applications randomly to see what is using all your resources try using **top** in terminal.  You can sort the listing by CPU usage by hitting upper case P, and memory usage with upper case M.  That will give you info on what is using all your CPU or memory, and then you can try to figure out why.

---

### Post by Bucky Ball on 2014-03-28
> **ajgreeny said:**
> Not seen that, but just for your info, rather than closing down applications randomly to see what is using all your resources try using **top** in terminal.  You can sort the listing by CPU usage by hitting upper case P, and memory usage with upper case M.  That will give you info on what is using all your CPU or memory, and then you can try to figure out why.

^^^
This. Also, how many tabs do you have open in Firefox? Please give more information about the specs of your machine. How much RAM and how big's the /swap partition?

---

### Post by ibjsb4 on 2014-03-28
Its old, but one idea (post#10)  disabled the nautilus thumbnail

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1069843](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1069843)

You could purge nautilus and run nemo for a while, to see if its really nautilus.

[https://launchpad.net/~webupd8team/+archive/nemo?field.series_filter=precise](https://launchpad.net/~webupd8team/+archive/nemo?field.series_filter=precise)

---

