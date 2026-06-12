---
title: "Slow dial-up connection - a fix?"
date: 2005-07-14
forum: Desktop Environments
---

### Post by indago on 2005-07-14
If you have the 'slow internet speed using dial-up' problem, try this - it worked for me:

In a terminal, type 

**stty**

 - it will show the serial port speed. Mine was set to 38400 baud.

If that's what you get, type 
[B]
stty 115200[/B]

and then 

**stty**

The port speed should now be 11520 baud.

I also edited the file **/etc/ppp/peers/provider**, (as root) to change the speed to 115200.

Mine is a pretty old modem - and was originally 38K, software-upgraded to 56K - could it be that it was detected as a slow modem during instalation???

Hope this helps - and hope the settings remain after re-booting...

---

