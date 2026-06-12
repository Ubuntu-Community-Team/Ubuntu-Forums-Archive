---
title: "Synaptic and Update Manager do not see Network, sudo apt does"
date: 2010-05-20
forum: Desktop Environments
---

### Post by anandnz on 2010-05-20
Hi 

I am using the Ubuntu 9.10 via vmware, on the windows XP desktop in office.  I have issues in having my synaptic manager and update manager working. I have proxy configured for the browser and internet seems working fine. 
I have added the proxy in the /etc/bash.bashrc, which got the sudo-apt install working, however i need help to get the synaptic manager and update manager working. Any help is appreciated. 
Things i did: I have searched in this forum and internet and removed the reference in apt.conf file 
Any ideas are welcome.

Cheers

---

### Post by anandnz on 2010-05-29
Oops this is solved, by having the right IP address in synaptic, preference and settings. 
Thank you all.

---

### Post by lisati on 2010-05-29
> **anandnz said:**
> Oops this is solved, by having the right IP address in synaptic, preference and settings. 
Thank you all.

Don't forget to mark the thread as "solved" using the "thread tools" link. :)

---

### Post by efflandt on 2010-05-29
Note that in X you can set proxy(s) under System > Preferences > Network Proxy, and whether to "Apply System-Wide...".

I had to do that when running Ubuntu at work, because they have our SonicWall blocking direct internet access of port 80 and 443, which have to go through the VPN to our factory (squid?) proxy.

---

