---
title: "Installation (RPM or debian)"
date: 2008-09-19
forum: Desktop Environments
---

### Post by MAbdullah47 on 2008-09-19
Hi

 I have ubuntu (8.04) server (installed) , I want to Install this VPN package:[http://wiki.openswan.org/index.php/Openswan/Install](http://wiki.openswan.org/index.php/Openswan/Install)

But Since I'm new in linux , which method in installation should I use is it (RPM) or (Debian) please let me know how to use the available tools inside (ubuntu) to install the (VPN) package?

---

### Post by Daisuke_Aramaki on 2008-09-19
apt method wud be ideal for ubuntu. and openswan packages are available in hardy.

just do this

```
sudo apt-get install openswan
```

it will take care of the additional packages that are needed. hope that helps.

---

### Post by anotherdisciple on 2008-09-19
> **Daisuke_Aramaki said:**
> apt method wud be ideal for ubuntu. and openswan packages are available in hardy.

just do this

```
sudo apt-get install openswan
```

it will take care of the additional packages that are needed. hope that helps.

Yes, doing it this way is better because you get all of the security updates... that's the beauty of the sources.list in ubuntu.

---

