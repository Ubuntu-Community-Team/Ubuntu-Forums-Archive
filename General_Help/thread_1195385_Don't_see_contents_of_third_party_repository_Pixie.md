---
title: "Don't see contents of third party repository: Pixie (open source Renderman)"
date: 2009-06-23
forum: General Help
---

### Post by hylas on 2009-06-23
So I'm running Ubuntu 9.04. I've tried this on two different machines with no success:

I added the repositories
```
deb http://ppa.launchpad.net/cedricpaille/pixie/ubuntu jaunty main
deb-src http://ppa.launchpad.net/cedricpaille/pixie/ubuntu jaunty main
```
listed at [https://launchpad.net/~cedricpaille/+archive/pixie]("https://launchpad.net/~cedricpaille/+archive/pixie") via the System->Administration->Software Sources dialog. I also added the PGP key in the Authentication tab. Even after a system restart, the package I expect to appear, pixie, is not avalailable in apt or synaptic. Is there any way to check that everything is kosher? Where might I be going wrong?

Thanks.
-hylas

---

### Post by michy99 on 2009-06-23
Have you done an update?```
sudo apt-get update
```I have had a situation where a third party package didn't show up in synaptic, but I could still install it with apt-get. I don't know why.

---

