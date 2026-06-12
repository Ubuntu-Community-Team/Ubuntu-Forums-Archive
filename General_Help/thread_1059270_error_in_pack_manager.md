---
title: "error in pack manager"
date: 2009-02-03
forum: General Help
---

### Post by vistadude on 2009-02-03
idk what the error is or what it means, but it says the fallowing:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and i did try running dpkg --configure -a but it did not work. How do i fix this?

---

### Post by avtolle on 2009-02-03
Open a terminal (Applications>Accessories>Terminal) and enter the following command```
sudo dpkg --configure -a
```input your password, of which you will not see any visual confirmation and, if you get additional errors, post them here. If there are no errors, then (still in the terminal) ```
sudo apt-get update && sudo apt-get upgrade
```. Be sure that Update Manager, Synaptic and/or Add/Remove are closed before beginning this.

---

### Post by vistadude on 2009-02-13
ok, sorry i took so long to reply, but i do get an error when i run sudo dpkg --configure -a, the error i get says 

```
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

```

---

### Post by vistadude on 2009-02-13
now this might have something to do with that error, i get a thing saying 
```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

```

so can any one tell me were to get this public key

---

### Post by forger on 2009-02-14
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by hikaricore on 2009-02-14
> **vistadude said:**
> now this might have something to do with that error, i get a thing saying 
```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

```

so can any one tell me were to get this public key

This error can pretty much be ignored btw.
It's more of a warning than anything else.

---

