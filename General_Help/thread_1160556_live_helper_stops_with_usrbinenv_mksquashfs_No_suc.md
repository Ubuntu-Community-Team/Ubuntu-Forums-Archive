---
title: "live helper stops with /usr/bin/env: mksquashfs: No such file or Directory"
date: 2009-05-15
forum: General Help
---

### Post by sythem on 2009-05-15
So I've made a live USB debian before without any problems whatsoever. Now I can't get it to run, at all. Here's what I did.
```
lh_config -d lenny -b usb-hdd --apt --bootstrap-flavour minimal --packages-lists "usbdrive"
```
And here's the ending of lh_build running on a fresh from scratch run.
```
P: Configuring file /etc/apt/sources.list
gpg: /root/.gnupg/trustdb.gpg: trustdb created
OK
Reading package lists... Done
Building dependency tree... Done
Reading package lists... Done
Building dependency tree... Done
debian-archive-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
P: Begin building root filesystem image...
/usr/bin/env: mksquashfs: No such file or directory
P: Begin unmounting filesystems...
```
Any clues to why it's giving me this issue?
Sorry, realized I don't use ubuntu anymore. I'll go post on debian's forums. But if someone could help here that would be cool.

---

