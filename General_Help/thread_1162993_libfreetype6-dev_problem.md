---
title: "libfreetype6-dev problem"
date: 2009-05-18
forum: General Help
---

### Post by rhaces on 2009-05-18
Hey, I'm trying to set up my blackberry in my Ubuntu Jaunty 64 bits, but for this to be done I need libfreetype6-dev but cant install it, here's what i get:

```
:~# apt-get install libfreetype6-dev 
Reading package lists... Done
Building dependency tree       be 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfreetype6-dev: Depends: libfreetype6 (= 2.3.9-4build1) but 2.3.9-4ubuntu0.1 is to be installed
E: Broken packages

```

I've tried apt-get install -f and has nothing to do

---

### Post by rhaces on 2009-06-12
Bump!!!, any answer?? please help

---

### Post by mc4man on 2009-06-12
Go to System -> Admin. -> Software Sources and under the 'Updates' tab make sure that the first 2 are enabled (security and updates

If not then enable, click close and reload. Then try again.

Alternatively go here for dl and install
[http://packages.ubuntu.com/jaunty-updates/libfreetype6-dev](http://packages.ubuntu.com/jaunty-updates/libfreetype6-dev)

(making sure this is installed first (appears to be already

[http://packages.ubuntu.com/jaunty-updates/libfreetype6](http://packages.ubuntu.com/jaunty-updates/libfreetype6)

---

### Post by rhaces on 2009-06-12
> **mc4man said:**
> Go to System -> Admin. -> Software Sources and under the 'Updates' tab make sure that the first 2 are enabled (security and updates

Nice, this made apt-get install libfreetype6-dev work perfectly

Thanks

---

