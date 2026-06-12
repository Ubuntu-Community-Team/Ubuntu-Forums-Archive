---
title: "New upgrade and some problems"
date: 2005-04-03
forum: Desktop Environments
---

### Post by Jad on 2005-04-03
Hi, 
I have just upgraded to hoary, its working fine, but still there is some troubles 
1) the result of "sudo apt-get update "
```
Reading package lists... Done
W: GPG error: ftp://ftp.nerim.net stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems
```

2) Webmin cannot be installed or removed (it was installed on my warty) as three of its packages marked as broken and cannot be auth to be installed (webmin-core, webmin-inetd,webmin-software)

```
jad@ubuntu:~ $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  cpudyn
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up webmin-core (1.180-2) ...
/etc/webmin/webmin.acl: No such file or directory
dpkg: error processing webmin-core (--configure):
 subprocess post-installation script returned error exit status 2
Setting up webmin-inetd (1.160-2) ...
/etc/webmin/webmin.acl: No such file or directory
dpkg: error processing webmin-inetd (--configure):
 subprocess post-installation script returned error exit status 2
Setting up webmin-software (1.160-2) ...
/etc/webmin/webmin.acl: No such file or directory
dpkg: error processing webmin-software (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 webmin-core
 webmin-inetd
 webmin-software
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please advise
Regards

---

### Post by Jad on 2005-04-03
**SOLVED**
the problem is with apt before it tries to install any other packages etc.
it tries to clear out its list of 'packages to configure post-install'
webmin got stuck because it couldnt find that file
so 
```
sudo touch /etc/webmin/update.conf && sudo apt-get remove webmin-core webmin-inetd webmin-software
```
will make apt statisfied :D

---

### Post by Jad on 2005-04-03
ah Many thanks to gh0st- #cpanel efnet.

---

### Post by wolovids on 2005-04-03
For number 1, did you try [this](http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary) ?

---

### Post by Jad on 2005-04-03
yeah and it works

---

### Post by saoday on 2005-04-14
I have the same problem but the above fix does this for me???  

Please help 

**apt-get remove webmin-core webmin-apache webmin-mysql webmin-procmail webmin-webalizer webmin-inetd webmin-xinetd**Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  webmin-apache webmin-core webmin-inetd webmin-mysql webmin-procmail webmin-webalizer
  webmin-xinetd
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 14.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 93579 files and directories currently installed.)
Removing webmin-apache ...
/var/lib/dpkg/info/webmin-apache.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-apache (--remove):
 subprocess pre-removal script returned error exit status 1
/var/lib/dpkg/info/webmin-apache.postinst: line 4: /usr/sbin/update-webmin: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing webmin-webalizer ...
/var/lib/dpkg/info/webmin-webalizer.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-webalizer (--remove):
 subprocess pre-removal script returned error exit status 1
Removing webmin-core ...
/var/lib/dpkg/info/webmin-core.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-core (--remove):
 subprocess pre-removal script returned error exit status 1
Removing webmin-inetd ...
/var/lib/dpkg/info/webmin-inetd.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-inetd (--remove):
 subprocess pre-removal script returned error exit status 1
Removing webmin-mysql ...
/var/lib/dpkg/info/webmin-mysql.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-mysql (--remove):
 subprocess pre-removal script returned error exit status 1
Removing webmin-procmail ...
/var/lib/dpkg/info/webmin-procmail.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-procmail (--remove):
 subprocess pre-removal script returned error exit status 1
Removing webmin-xinetd ...
/var/lib/dpkg/info/webmin-xinetd.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-xinetd (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
[B] webmin-apache
 webmin-webalizer
 webmin-core
 webmin-inetd
 webmin-mysql
 webmin-procmail
 webmin-xinetd[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by XDevHald on 2005-04-14
Since we're on the new updates deal of errors, I am getting the following error when doing an update on my java that have new upgrades

[b]The following packages have unmet dependencies:
[/b]  libjava-gnome-doc: Depends: libgtk-java but it is not installable
                     Depends: libgnome-java but it is not installable
                     Depends: libgconf-java but it is not installable
                     Depends: libglade-java but it is not installable

I have been trying by myself to figure this out, but I can't seem to do it on my own anymore, is there a solution to this issue?

---

### Post by Bug on 2005-04-20
Thanks, I've been trying to figure out fix this!

Adam

---

