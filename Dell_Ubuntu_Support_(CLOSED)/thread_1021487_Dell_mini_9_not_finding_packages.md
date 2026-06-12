---
title: "Dell mini 9 not finding packages"
date: 2008-12-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gondee on 2008-12-25
I just installed Ubuntu 8.10 on my Dell mini 9 (64 gig) and i was trying to install the codecs but when i try to install anything. it says package cannot be found.

What should i do. 

Heres what it says on the codecs

Couldn't find package ubuntu-restricted-extras

---

### Post by lswest on 2008-12-25
go to System-->administration-->software sources and make sure the CD repo is unchecked, and enable multiverse and universe repos if they aren't already enabled.  Make sure you're connected to the internet then try: ```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Gondee on 2008-12-25
Thanks it worked great!!! i have never had to do that before

---

### Post by lswest on 2008-12-26
Yeah, happens to me occasionally, that the repos haven't been checked for packages yet, and that it won't find packages then.

Glad it worked!
Lswest

Basically sudo apt-get update queries the repos for package lists, and then the packages can be found for installation (which is why you need to update packagelists before upgrading packages, since the new package lists have the new package versions).

---

