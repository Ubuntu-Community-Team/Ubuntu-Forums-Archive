---
title: "how to install /sbin/service"
date: 2009-05-29
forum: General Help
---

### Post by aniketto on 2009-05-29
I am using Ubuntu8.04 LS.
I want to install /sbin/service package on my Ubuntu.
 
When I tried to install it using 
#apt-get install sysvconfig
but then it got installed in /usr/bin/service
 
I strictly want it as /sbin/ service , so as not to change deployment file in an application.
 
Can somebody tell me how I can I do that.
 
Thanks,
Aniket

---

### Post by sehe on 2009-06-03
I'd say, symlinks are your friend

ln -sfv /usr/local/sbin/service /sbin/service

If you really must have it out-of-the-box, I can point at checkinstall to 'record' your custom .deb. Seems like overkill to me.

You could also

sudo apt-get build-dep sysvconfig
apt-get source sysvconfig

and modify the deb sources directly

---

