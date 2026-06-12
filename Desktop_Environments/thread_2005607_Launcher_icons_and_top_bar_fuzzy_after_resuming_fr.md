---
title: "Launcher icons and top bar fuzzy after resuming from sleep mode"
date: 2012-06-17
forum: Desktop Environments
---

### Post by vb10000 on 2012-06-17
Ubuntu 12.04 (64 bit) installed recently and works fine except:

Launcher and top bar icons become fuzzy when the computer is brought out of suspend mode. I can click on a fuzzy icon (say firefox) and the browser window that opens up is fine.

Do others have this issue, and if so, how was is resolved?

---

### Post by Call_M on 2012-06-19
Here the same problem. 

I am not sure if it also started after suspending, but could be plausible since recently for the first time I suspended the OS.

Anyone some tips to get rid of the blurry icons?

---

### Post by vb10000 on 2012-06-22
I found the following command for a temporary fix. Open a terminal to use it.

unity --replace &

This is not a permanent fix.

---

### Post by Call_M on 2012-06-22
Thanks vb1000
However tried it but it didn't work for me. 

It looks like it is an reported bug:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/977147](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/977147)

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/987023](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/987023)

The importance level is set to low and medium.

Hopefully some other users comes with a workable solution.

---

