---
title: "upgrading errors 8.04 - 8.10"
date: 2009-04-07
forum: General Help
---

### Post by qaazaa on 2009-04-07
Hi my fellow ubuntu users i have come up against a problem when trying to upgrade ubuntu online through there update manager and even via command every server i try it seems to give me this error:::

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

and a few more and now even my sound says i dont have a no volume gstreamer

plus i tried doing it from image file but nothing seems to happen

---

### Post by Partyboi2 on 2009-04-08
Open a terminal (Applications>Accessories>Terminal) and try reinstalling ubuntu-keyring
```
sudo apt-get install --reinstall ubuntu-keyring
```
```
sudo apt-get update
```

---

