---
title: "Unity greeter startup script on Trusty Tahir?"
date: 2014-04-21
forum: Desktop Environments
---

### Post by jcllings on 2014-04-21
So what I want to do is run a script on startup that starts the synergy daemon. I want it to run automagically when the system starts in GUI mode even if no one actually logs in. I have a script for this but in the past it was run from /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf.  This doesn't do the trick since I upgraded today to Trusty Tahir. 

What is the Trusty Tahir equivalent to /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf ?

Update: The above is apparently the wrong question. It *is* launching but it drops dead whereas it did not before.

Jim C.

---

### Post by jcllings on 2014-04-21
OK, I got it sorted out.  On a hunch, I added a 5 second sleep to the script because this machine is so ridiculously fast (maxed memory, SSD, latest CPU, etc. ).  This fixed the problem. Later I was able to narrow it down to 3 seconds.

---

