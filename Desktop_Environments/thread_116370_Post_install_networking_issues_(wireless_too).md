---
title: "Post install networking issues (wireless too)"
date: 2006-01-12
forum: Desktop Environments
---

### Post by KermitJr on 2006-01-12
Hi all.

While installing Kubuntu, I had to skip the networking setup of the installer.

One booted, I had a signal via Kwifi but couldn't get an IP.

```
sudo dhclient ra0

```
ra0 is my wlan0.  You try eth0, wlan0 or whatever your output is of 

```
sudo iwconfig
sudo ifconfig
```

I didn't have to resort to this in Ubuntu when I skipped it... only Kubuntu.

Cheers,
KermitJr

---

