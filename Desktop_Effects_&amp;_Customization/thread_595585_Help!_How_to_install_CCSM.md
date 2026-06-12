---
title: "Help! How to install CCSM?"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by Ian93 on 2007-10-28
Okay, I've recently upgraded to 7.10, and I am wondering how to install the Compiz Config Settings Manager.

I've tried other threads, but when I terminal codes like:
sudo apt-get install compizconfig-settings-manager

I get this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

Synaptic Package Manager brings up nothing when I search for compizconfig-settings-manager.
I also think there are aptitude codes.

Help will greatly be appreciated.

---

### Post by mrmiserable on 2007-10-28
you need to enable repositories for ccsm
system>administration>software sources

best of luck

---

### Post by Ian93 on 2007-10-28
I can't believe I missed that.
Thanks a lot.

I must really be out of it tonight.

---

### Post by mrmiserable on 2007-10-28
enjoy tweaking compiz

---

### Post by Blario on 2008-03-27
Geez.... Which software repository is it?  It appears that all mine are checked.

except: 
Pre-released updates (gutsy-proposed)
Unsupported updates (gutsy-backports) (I'd think ubuntu is supporting compiz-fusion now....)
& The archive source code......

---

### Post by daniel7860 on 2008-06-23
ok when i type : apt-get install compizconfig-settings-manager

it says i have to be root to do that, how to i bypass that crap?:guitar:

---

### Post by daniel7860 on 2008-06-23
never mind yall, i fixed it. :guitar:

---

### Post by eryksun on 2008-06-23
> **daniel7860 said:**
> ok when i type : apt-get install compizconfig-settings-manager

it says i have to be root to do that, how to i bypass that crap?:guitar:

```
sudo apt-get install compizconfig-settings-manager
```

P.S. It's not crap. ;-)

---

