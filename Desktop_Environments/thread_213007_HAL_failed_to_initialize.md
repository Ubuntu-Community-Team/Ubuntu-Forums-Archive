---
title: "HAL failed to initialize"
date: 2006-07-10
forum: Desktop Environments
---

### Post by lifeboy on 2006-07-10
I have upgraded Breezy to Dapper and for some unknown reason I have a problem with HAL.  It causes quite a few problems, but all seem to be related to some form of disk mounting.  I've googled it, but can't find much in the line of what I'm experiencing.  Attached is the relevant part of my syslog and my fstab.  (renamed with .txt extension since the forums don't allow all files)

Samba mounts don't work for one, and also samba shares I cannot connect to.

Reinstalling HAL does not help.  When starting up, the boot process takes very long (up to 5 minutes) at "starting HALD" as well, but I can't find a line relating to that in syslog?

Does anybody now what is going wrong here?

Thanks

---

### Post by sebastjanp on 2006-07-12
I believe that the problem is caused by samba shares. I had the sam e problem and I have bypassed it with using NFS for file sharing on my server and client (both Ubuntu).

If you will do the same:
[LINK](https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29)
[LINK](https://help.ubuntu.com/ubuntu/serverguide/C/network-file-system.html)

---

### Post by lifeboy on 2006-07-12
Well, I connect to three windows shares from this machine, so unless I can get NFS going on Windows, I can't do this.

Furthermore I have now noticed that when I do "/etc/init.d/dbus restart" it stops hald and dbus, then restarts dbus and then takes about 5 minutes attempting to start hald and doesn't succeed:

run-parts: /etc/dbus-1/event.d/20hal exited with return code 2

I'm going to remove all the samba mounts from /etc/fstab and test again.  Then I'll put them back and see if it still happens.

---

