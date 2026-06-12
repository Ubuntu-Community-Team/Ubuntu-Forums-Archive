---
title: "webmin reomval"
date: 2005-07-12
forum: Desktop Environments
---

### Post by SteveGodfrey on 2005-07-12
I installed webmin by downloading the gzip file from the webmin site and then running the setup.sh script. After doing this webmin worked fine,, I then wanted to install the webmin-squid add-on but I did this via the synaptic gui. Unfortunately this also installed the unbuntu version of webmin. I then run the webmin uninstall script but this seems to have messed up synaptic. I can't install or remove webmin! Please help....

root@ubuntu:/home/steve # apt-get remove webmin
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  webmin webmin-squid
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7565kB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 70695 files and directories currently installed.)
Removing webmin-squid ...
/etc/webmin/webmin.acl: No such file or directory
dpkg: error processing webmin-squid (--remove):
 subprocess pre-removal script returned error exit status 2
/etc/webmin/webmin.acl: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Removing webmin ...
Errors were encountered while processing:
 webmin-squid
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/home/steve #

---

### Post by varunus on 2005-07-12
Use synaptic to reinstall the webmin ubuntu package, then uninstall it.

---

### Post by SteveGodfrey on 2005-07-12
[QUOTE=varunus]Use synaptic to reinstall the webmin ubuntu package, then uninstall it.[/QUOTE]
 E: webmin-squid:  subprocess pre-removal script returned error exit status 2

---

### Post by ameerirshad on 2005-08-06
Yup I got the same problem and the same error! I can't access webmin, so I can't remove or update it using their site, and I can't reinstall and/or remove webmin, as it gives the same error! I posted it [here ]("http://ubuntuforums.org/showthread.php?postid=287309#poststop")as well, but I saw that was for wharty :-?

I would love to see a solution :|

---

### Post by C38a7r1zvl on 2005-08-06
Try installing webmin via dpkg directly (with the use of some force options if necessary -> man dpkg) and then uninstall it the same way, that should give you a clean removal. Do a dpkg --purge webmin* afterwards and you're done.

Anyway installing webmin via the installer and webmin-addons via dpkg is a bad idea. Webmin has its own module installer, use this one the next time or dpkg for *everything*.

---

### Post by ameerirshad on 2005-08-07
succeeded........ \\:D/

---

