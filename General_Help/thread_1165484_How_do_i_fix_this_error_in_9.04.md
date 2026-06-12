---
title: "How do i fix this error in 9.04?"
date: 2009-05-20
forum: General Help
---

### Post by hatewindows on 2009-05-20
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This is the error i get when i open Synaptic Package Manager

Thanks for any help.. MARK

---

### Post by camper365 on 2009-05-20
It seems to me that synaptic (or aptitude or apt-get or the Add/Remove from the Applications menu or the update manager) got killed while it was installing software.
All you need to do is run
```
sudo dpkg --configure -a
```and it should work.
Depending on what you were doing, you may have issues with one package.
What I have done before is
```
sudo aptitude purge *package*
```and then
```
sudo aptitude install *package*
```

---

### Post by paradigm2 on 2009-05-20
I wonder why since 9/10 timesjust issuing the given command does the trick we do not just pop up something asking the user if we should try to fix it for them?

This is a very common thing and IMO one of the things that say my mother would have trouble with if she were to move to Ubuntu from Vista.  I see a lto of posts like this in the forum....

---

