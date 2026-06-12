---
title: "Can't install firefox"
date: 2007-07-30
forum: Desktop Environments
---

### Post by rkakkar on 2007-07-30
```
$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxgtk2.8-0 libwxbase2.8-0 libcrypto++5.2c2a libgift0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnspr4 libnss3
Suggested packages:
  firefox-gnome-support latex-xft-fonts firefox-libthai
The following NEW packages will be installed:
  firefox libnspr4 libnss3
0 upgraded, 3 newly installed, 0 to remove and 60 not upgraded.
Need to get 10.2MB of archives.
After unpacking 31.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://security.ubuntu.com feisty-security/main libnspr4 2:1.firefox2.0.0.4+1-0ubuntu1
  404 Not Found
Err http://security.ubuntu.com feisty-security/main libnss3 2:1.firefox2.0.0.4+1-0ubuntu1
  404 Not Found
Err http://security.ubuntu.com feisty-security/main firefox 2.0.0.4+1-0ubuntu1
  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox2.0.0.4+1-0ubuntu1_i386.deb  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox2.0.0.4+1-0ubuntu1_i386.deb  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.4+1-0ubuntu1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I'm using Kubuntu.

---

### Post by Cyberapoc on 2007-07-30
Like the error suggest, try to run 'sudo apt-get update' and then 'sudo apt-get install firefox'. This should work. Or go to System->Administration->Synaptic and search for firefox

If this doesn't work, download it from here [http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)
or get opera or epiphany web browser.

---

