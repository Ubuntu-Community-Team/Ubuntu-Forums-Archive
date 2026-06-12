---
title: "FWUPD: Unsupported daemon version"
date: 2019-12-21
forum: Desktop Environments
---

### Post by amilopowers on 2019-12-21
Hello

When I run ```
fwupdmgr get-updates
``` I get the following error: ```
Unsupported daemon version 1.3.5, client version is 1.2.10
```.

Does anyone know how to fix this?

Gnome Software says that fwupd is version 1.3.5 but I am not sure if client or daemon is meant.

---

### Post by oldfred on 2019-12-22
apt show fwupdate
Description: Tools to manage UEFI firmware updates

apt show fwupd
Description: Firmware update daemon

man fwupdmgr

What do these show?
       sudo fwupdmgr get-devices
sudo fwupdmgr get-updates
sudo fwupdmgr update

---

