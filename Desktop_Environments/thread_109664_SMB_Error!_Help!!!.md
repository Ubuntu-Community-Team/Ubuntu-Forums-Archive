---
title: "SMB Error! Help!!!"
date: 2005-12-29
forum: Desktop Environments
---

### Post by katiad on 2005-12-29
I've had samba working for a couple months now, but after a power outage, I now get a strange error...

The setup:

Trying to access windows network shares from linux. Example sharename; dublin. Fstab hasn't changed a bit since I set it up and had it working great, smbcredientals is still there and all information is correct. The mount points are available and set up properly - nothing's changed, but now they refuse to mount. 

Doing a sudo mount -a gives me this error for each share mounted:

9424: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

I need these shares! Please help!

---

