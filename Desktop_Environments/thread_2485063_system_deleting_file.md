---
title: "system deleting file"
date: 2023-03-18
forum: Desktop Environments
---

### Post by helotbc-0 on 2023-03-18
Good evening, I am running Ubuntu 22.04.2 LTS on a Lenovo Yoga 7.2. My issue is that I've installed a driver to run a smart card reader. This config works perfectly. The issue is that the driver file, /usr/lib64/libcackey.so, is periodically deleted by the system. I need help identifying what is deleting this file, and possibly, when. I have looked through the logs and I have seen nothing which could be the culprit. Any thoughts would be helpful.

I have attached the log from the last 24hrs and during this period, the file was deleted.

Thx.

---

### Post by helotbc-0 on 2023-04-07
After some observation, I determined that APT was upgrading the "cackey" package and deleting the file I was using, libcackey.so. I found the driver it was installing, /usr/lib/cackey.so. Unfortunately, this new driver made Firefox crash. To stop APT from upgrading the software, I created a "preferences" file, /etc/apt/preferences. In this file I entered a configuration to stop APT from upgrading the software to v0.7.11:

Package: cackey
Pin: version 0.7.11-1
Pin-Priority: -1

Ref APT_PREFERENCES(5)  for further information.

---

