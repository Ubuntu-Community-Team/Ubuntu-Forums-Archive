---
title: "Firefox cannot be removed from 9.10 to 10.04"
date: 2010-05-04
forum: Desktop Environments
---

### Post by princekoj on 2010-05-04
Hello,

I installed unbuntuzilla in 9.10 and kept an update of firefox from  Mozilla. After one update firefox 3.6.3 refused to start except in safe mode. Also attempts to remove firefox was unsuccessful, even when I upgraded to Ubuntu 10.04. Please see the printout below which I got when I ran sudo aptitude remove-firefox-mozilla-build.

I cannot update my system at the moment either as Synaptic cannot go beyond trying to remove firefox.

Please help.

-------------------------
princekoj@princekoj-laptop:~$ sudo aptitude remove firefox-mozilla-build
[sudo] password for princekoj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  firefox-mozilla-build 
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 178562 files and directories currently installed.)
Removing firefox-mozilla-build ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
  found `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error processing firefox-mozilla-build (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 firefox-mozilla-build
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

------------------

Regards

Princekoj

---

### Post by tgalati4 on 2010-05-04
You probably have a symbolic link to ubuntu's firefox.

which firefox

ls -la /usr/bin/fire*

If it's a symbolic link, then rename it to fireold

sudo mv /usr/bin/firefox /usr/bin/fireold

Then try your removal.

---

### Post by lovinglinux on 2010-05-05
[http://ubuntuforums.org/showpost.php?p=9145890&postcount=13](http://ubuntuforums.org/showpost.php?p=9145890&postcount=13)

---

### Post by princekoj on 2010-05-05
Renamed symbolic link and Got this message in Synaptic:
E: firefox-mozilla-build: subprocess installed post-removal script returned error exit status 2

The message in the terminal - 
princekoj@princekoj-laptop:~$ sudo aptitude remove firefox-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  firefox-mozilla-build 
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 178524 files and directories currently installed.)
Removing firefox-mozilla-build ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
  found `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error processing firefox-mozilla-build (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 firefox-mozilla-build
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
 ---------------------------------

Thanks for your help so far.

Princekoj

---

### Post by princekoj on 2010-05-05
Still did not work when I tried your command to remedy the "divert." Thanks for you attempt. Any other suggestion?

Princekoj

---

### Post by lovinglinux on 2010-05-06
> **princekoj said:**
> Still did not work when I tried your command to remedy the "divert." Thanks for you attempt. Any other suggestion?

Princekoj

Contact [nanotube](http://ubuntuforums.org/member.php?u=66474) for support. This is an Ubuntuzilla related problem.

---

### Post by nanotube on 2010-05-06
Hi

It seems you have a local diversion, which is interfering with the firefox-mozilla-build package diversion.

This is probably from you trying to use both the ubuntuzilla script and the ubuntuzilla repository to install, or something like that...

at any rate, remove the local diversion with this command:
```
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

after that, i think you should be able to uninstall firefox-mozilla-build package.

---

### Post by princekoj on 2010-05-07
Thank you very much nanotube,

This is absolutely sweet. I am back in business. I am really greatful.

Princekoj

---

### Post by nanotube on 2010-05-08
> **princekoj said:**
> Thank you very much nanotube,

This is absolutely sweet. I am back in business. I am really greatful.

Princekoj

Glad i could help - have fun. :)

---

