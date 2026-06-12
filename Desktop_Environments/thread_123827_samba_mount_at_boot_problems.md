---
title: "samba mount at boot problems"
date: 2006-01-31
forum: Desktop Environments
---

### Post by harryllee on 2006-01-31
I've had samba mounting my terabyte library (which is a workgroups flavored share) but not having it be a part of my file system, so, I did all the steps in the easy guide, and it barfed. halp!
[4295472.691000] ra0: no IPv6 routers present
[4295478.243000] NET: Registered protocol family 17
[4295488.410000] ra0: no IPv6 routers present
[4297911.222000] smbfs: mount_data version 1684370019 is not supported
[4298047.205000] smbfs: mount_data version 1684370019 is not supported
[4298345.327000] smbfs: mount_data version 1684370019 is not supported
[4299085.618000] smbfs: mount_data version 1919251317 is not supported
[4299155.474000] smbfs: mount_data version 1919251317 is not supported

---

### Post by Gabbe on 2007-09-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/50651](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/50651) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had the same problem and in desperation I installed all things samba in the repositories, and the error vanished. I have retraced my steps, made some test and my conclusion is that installing the package smbfs solves the problem, that is try doing a [FONT="Lucida Console"]sudo apt-get install smbfs[/FONT] and problem should disappear. 

Why this works I dont know since Nautilus does not need this package to mount samba shares, perhaps someone can enlighten us? 

Note that there's in an reopened bug case in launchpad, #50651, for what seems to be the same problem.

---

