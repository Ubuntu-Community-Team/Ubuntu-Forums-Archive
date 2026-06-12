---
title: "ATI Radeon HD 4800 fglrx no desktop effects"
date: 2010-11-22
forum: Desktop Environments
---

### Post by rmills on 2010-11-22
I've installed the fglrx drivers out of the repo.  That worked the first time I restarted my computer.  The second time I restarted my computer, the drivers were still enabled, but I couldn't enable desktop effects.

So I uninstalled the drivers from the repo, and tried the ones on the AMD/ATI site.  Same deal - worked after first restart, didn't after second restart.

I've run through all the solutions posted here:
[http://ubuntuforums.org/showthread.php?t=1466085](http://ubuntuforums.org/showthread.php?t=1466085)
and here:
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
and here:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Someone please help.  I'm using the default mesa drivers right now and I feel like I'm wasting the power of my video card.

Here's some relevant info:
```
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV790 [Radeon HD 4800 Series]

```

```
$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  157 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  20
  Current serial number in output stream:  20
```

---

