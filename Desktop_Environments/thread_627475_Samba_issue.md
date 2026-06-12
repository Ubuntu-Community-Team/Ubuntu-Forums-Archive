---
title: "Samba issue"
date: 2007-11-30
forum: Desktop Environments
---

### Post by benbooth on 2007-11-30
I'm having trouble getting a Samba share to work without any security.
I currently logon to a Windows domain, and I would like a linux server to act as the fileserver. I have decided to not use a domain anymore as it isn't worth the hassle. So eventually it will be removed and everyone will log on locally and have access to the Linux Samba share.

At the moment no matter what I seem to change in smb.conf make no difference and I cannot wither logon to Samba share or if I enable guest it's read-only.

Is this a conflict between Windows accounts and the samba share?

Is it possible to just share to everyone with read-write permission on the share?

Thanks,

Ben

---

### Post by TeaSwigger on 2007-11-30
Samba was a big pain in the eh... well you know, to me. What you want is possible though. 

Have you seen Stormbringer's guide?
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
And this was also helpful to me:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

If you need specific help you'll need to post specific info. For instance the smb.conf file (change names as you like) and the desired network configuration.

---

