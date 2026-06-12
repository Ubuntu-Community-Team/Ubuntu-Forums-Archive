---
title: "Desktop 10.04 cant join active directory"
date: 2010-06-01
forum: Desktop Environments
---

### Post by delineator on 2010-06-01
Hello,

I have been using Ubuntu for a little over a year now and I find it fanastatic!

But here is my problem... I have a windows 2003 server mini tower ATX running VMware workstation 7.0 that has a Ubuntu server 32-bit and a Ubuntu desktop; both versions are 10.04. Now, my ubuntu server edition joins active directory just fine, but my ubuntu desktop does not. I have checked some of the forums for my specific problem but to no avail.

Here is my /etc/samba/smb.conf file:

[Global]

workgroup = XXXXDELIGHT
security = ads
realm = XXXXDELIGHT.BIZ
idmap backend = lwopen
idmap uid = 50-9999999999
idmap gid = 50-9999999999
winbind use default domain = yes
winbind enum users = yes
winbind enum groups = yes
template shell = /bin/bash
template homedir = /home/%U

---

