---
title: "Steam Missing 32-bit Library"
date: 2016-10-24
forum: Gaming &amp; Leisure
---

### Post by crdis2 on 2016-10-24
I've had Steam on my computer for a while, but recently it has stopped working because it says it's missing the libc.so.6 32-bit library. I'm on Ubuntu 16.04 LTS, does anyone know how to fix this?:confused:

---

### Post by slickymaster on 2016-10-24
Hi crdis2, welcome to the forums.

Have you already tried to install the missing library?```
sudo apt-get update
sudo apt-get install libc6-i386
```

---

### Post by crdis2 on 2016-10-24
Yes, I just tried this, but the terminal said that there are some packages with unmet dependencies and it told me to use apt-get -f install. I tried this and then the terminal said: ***E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission Denied)***. Then below that: ***E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?***

---

### Post by slickymaster on 2016-10-24
> **crdis2 said:**
> Yes, I just tried this, but the terminal said that there are some packages with unmet dependencies and it told me to use apt-get -f install. I tried this and then the terminal said: ***E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission Denied)***. Then below that: ***E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?***

Did you forget to put ```
sudo
``` before the```
apt-get -f install
```

---

