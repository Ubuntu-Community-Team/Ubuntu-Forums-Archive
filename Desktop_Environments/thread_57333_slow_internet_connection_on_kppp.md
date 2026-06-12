---
title: "slow internet connection on kppp"
date: 2005-08-16
forum: Desktop Environments
---

### Post by ippiraman on 2005-08-16
I can successfully connect to the internet through a dial-up connection with kppp. No problem there, but whenever I run update or install a new package through apt-get, I experience very very slow browsing. All the time, it fails to resolve the domain name. So I usually let apt-get update/upgrade/install to finish before I can fully surf the web. Is this normal or is there any kernel "tweak" that I could use?

Thanks.

---

### Post by coolclassic on 2005-08-16
When installing new software apt will download the latest versions from the repositories this is done by using the internet. As you are using the internet at the same time you are effectively slowing your connection this is completly normal.

---

