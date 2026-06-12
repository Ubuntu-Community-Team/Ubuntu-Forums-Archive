---
title: "cloud-init v.0.7.9 issue"
date: 2017-09-21
forum: Fedora/RedHat and derivatives
---

### Post by vineetmadan on 2017-09-21
Hello,

We are using cloud-init to pass on some user data scripts into our AWS EC2 server's (CentOS 7.3) at run time (cloud-init v0.7.5 being used here).  However while upgrading to CentOS 7.4 we observed that cloud-init auto upgrades from v0.7.5 to v0.7.9 via yum update and rebooting the instance. Now with cloud-init v.0.7.9, we are seeing some indifferent logs like below:

util.py[DEBUG]: Running command ['mount', '-o', 'ro,sync', '-t', 'iso9660', '/dev/xvda', '/tmp/tmpWMbkYg'] with allowed return codes [0] (shell=False, capture=True)
util.py[DEBUG]: Running command ['blkid', '-odevice', '/dev/sr0'] with allowed return codes [0, 2] (shell=False, capture=True)
util.py[DEBUG]: Running command ['blkid', '-odevice', '/dev/sr1'] with allowed return codes [0, 2] (shell=False, capture=True)
util.py[DEBUG]: Running command ['blkid', '-tTYPE=vfat', '-odevice'] with allowed return codes [0, 2] (shell=False, capture=True)
util.py[DEBUG]: Running command ['blkid', '-tTYPE=iso9660', '-odevice'] with allowed return codes [0, 2] (shell=False, capture=True)
util.py[DEBUG]: Running command ['blkid', '-tLABEL=cidata', '-odevice'] with allowed return codes [0, 2] (shell=False, capture=True)
__init__.py[DEBUG]: Seeing if we can get any data from <class 'cloudinit.sources.DataSourceConfigDrive.DataSourceConfigDrive'>
util.py[DEBUG]: Running command ['blkid', '-odevice', '/dev/sr0'] with allowed return codes [0, 2] (shell=False, capture=True)
util.py[DEBUG]: Running command ['blkid', '-odevice', '/dev/sr1'] with allowed return codes [0, 2] (shell=False, capture=True)
util.py[DEBUG]: Running command ['blkid', '-odevice', '/dev/cd0'] with allowed return codes [0, 2] (shell=False, capture=True)
util.py[DEBUG]: Running command ['blkid', '-odevice', '/dev/cd1'] with allowed return codes [0, 2] (shell=False, capture=True)
util.py[DEBUG]: Running command ['blkid', '-tTYPE=vfat', '-odevice'] with allowed return codes [0, 2] (shell=False, capture=True)

But we are no longer able to see the output of our user data scripts which we were able to see earlier. Due to this, we cannot debug any errors in our user data scripts by looking at logs. We can hold on OS version for now, but we'll eventually have to move to the newer one and cope up with cloud-init v.0.7.9. Did anyone else face a similar problem or if someone could suggest a resolution to:
1. Stop the upgrade from cloud-init v.0.7.5 to v0.7.9
2. We can see the user data logs in the server.

Regards,
Vineet

---

### Post by QIII on 2017-09-21
Moved to Fedora/Redhat and Derivatives.

The Forum Feedback and Help section is not a general support area.

---

