---
title: "Synaptic package manager problem"
date: 2006-07-28
forum: Desktop Environments
---

### Post by while on 2006-07-28
Im seeing the following on my IBM laptop t41 no matter what package I try and install or de-install...... some of the packages seem to work but im not sure they work 100% and others do not work at all....  Any help would be greately appriciated. 

Thanks

William 

Upgrading trigger, response and rpc files ...
Running Online Update for fingerprints, connecting to [www.thc.org/thc-amap](www.thc.org/thc-amap)
Error: could not resolve host: [www.thc.org](www.thc.org)
dpkg: error processing amap (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 amap
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up amap (4.8-1.1) ...
Upgrading trigger, response and rpc files ...
Running Online Update for fingerprints, connecting to [www.thc.org/thc-amap](www.thc.org/thc-amap)
Error: could not resolve host: [www.thc.org](www.thc.org)
dpkg: error processing amap (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 amap

---

### Post by h2gofast on 2006-07-28
> Error: could not resolve host: [www.thc.org](www.thc.org)
This usually means that particular repository is down, doesn't exist, or you simply aren't connected to the internet.

---

### Post by while on 2006-07-28
yeah that I got... but I am connected, however that host doesnt seem to exist..... my desktop with the same version doesnt get this error.... 

any idea where this thc.org might be located in the config so I can remove/comment it out? 

Thanks

---

### Post by rbalfour on 2006-07-28
check the file/

/etc/apt/sources.list

---

### Post by while on 2006-07-28
nope not in there..... I have no idea where this is located.... It appears that its a problem with dpkg and not synaptic... I get the exact same erroe with apt-get install.....  im still looking and will post as I find anything..... and hopefully someone can give me insight as well....

---

### Post by while on 2006-07-28
this is actually an issue with the amap package...... I have uninsalled amap and now all seems to be well.....

---

