---
title: "Need Assitance Installing Alephone/Marathon"
date: 2010-12-23
forum: Gaming &amp; Leisure
---

### Post by Qualia on 2010-12-23
Has anyone else ran into this problem when installing Alephone? I just tired running ./configure on it only to have it stop with the message:

"configure: error: in `/home/spearmint/Aleph/AlephOne':
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details."

I always get the same message...any idea as to what I'm doing wrong?

---

### Post by iamanidiot123 on 2011-07-24
It might be because you don't have a compiler.  Do you have a c++ compiler? g++ is what most people (probably everybody) uses.  The package is called g++.  (i'm not sure if this is the problem.)


```
sudo apt-get install g++ build-essential
```
it will prompt for you to install a long list of stuff.

---

