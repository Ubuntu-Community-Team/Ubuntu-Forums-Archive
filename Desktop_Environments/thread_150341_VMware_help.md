---
title: "VMware help"
date: 2006-03-25
forum: Desktop Environments
---

### Post by roostishaw on 2006-03-25
Hello, 
How can I uninstall VMware so that I can re-install it properly as root?

Update: I found and ran the uninstaller in the bin folder. Then I logged on as root and tried the install again. Here is what I got:
```

root@roostishaw:~# sudo /home/roostishaw/vmware-player-distrib/vmware-install.pl
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin] /usr/bin

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc] /etc

What is the directory that contains the init scripts?
[/etc/init.d] /etc/init.d

Unable to copy the source file ./installer/services.sh to the destination file
/etc/init.d/vmware.

Execution aborted.

root@roostishaw:~#

```

Anyone know what's wrong?
Thanks!

---

