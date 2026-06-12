---
title: "file cannot be removed, uninstalled or deleted."
date: 2010-07-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bill56 on 2010-07-20
Hello everyone. I am very frustrated, because I get the same error message every time I try to get rid of file brscan.  How can I remove, uninstall or delete a file that keeps on saying there is no such file or directory? Please help.

bill@bill-desktop:~$ sudo apt-get install brscan checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
brscan is already the newest version.
The following extra packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch
  xz-utils
Suggested packages:
  gettext debian-keyring debian-maintainers g++-multilib g++-4.4-multilib
  gcc-4.4-doc libstdc++6-4.4-dbg libstdc++6-4.4-doc diffutils-doc
The following packages will be REMOVED:
  brscan
The following NEW packages will be installed:
  build-essential checkinstall dpkg-dev fakeroot g++ g++-4.4
  libstdc++6-4.4-dev patch xz-utils
0 upgraded, 9 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 8,521kB of archives.
After this operation, 27.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libstdc++6-4.4-dev 4.4.3-4ubuntu5 [1,522kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main g++-4.4 4.4.3-4ubuntu5 [5,756kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main g++ 4:4.4.3-1ubuntu1 [1,450B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main xz-utils 4.999.9beta+20091116-1 [233kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main patch 2.6-2ubuntu1 [121kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main dpkg-dev 1.15.5.6ubuntu4.1 [653kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main build-essential 11.4build1 [7,278B]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe checkinstall 1.6.1-10 [127kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main fakeroot 1.14.4-1ubuntu1 [101kB]
Fetched 8,521kB in 10s (788kB/s)                                               
(Reading database ... 154774 files and directories currently installed.)
Removing brscan ...
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHLFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHMFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHminiFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLe': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLeFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory
dpkg: error processing brscan (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan
E: Sub-process /usr/bin/dpkg returned an error code (1)
bill@bill-desktop:~$

---

### Post by bobcollard on 2010-07-23
First, do a search to find the file or package in your "File Manager" (Ctrl F).  If you find it, use the full location to remove it.  **Example**:
```
sudo apt-get remove /usr/bin/brscan
```

---

### Post by mikewhatever on 2010-07-24
You could try the 'apt-get remove' command instead of apt-get install. What makes you think that installing a package will remove it?

---

### Post by jarviser on 2010-07-24
It does not say that brscan does not exist! The files not found are sane scanner drivers in subdirectories, which may not have been properly installed in the first place, and are only being uninstalled because it presumably started to install before it noticed you already had brscan installed (or partially installed).

The muddle of responses is because 
1) brscan is already installed and you used apt-get install command
2) checkinstall was not installed with all its dependencies and that would best have been installed using synaptic package manager, and
3) as already said apt-get remove would surely be the command to use if you want to uninstall brscan (or do we misunderstand?)  What happens if you do that?

---

### Post by bill56 on 2010-07-28
Thanks guys. I found the file in the file system and removed it.

Bill

---

### Post by Andavane on 2010-08-08
Isee this is marked as SOLVED, however I'm getting almost identical after trying to install scanner, viz:

> andavane@andavane-vaayubuntu:~$ sudo apt-get install -f
[sudo] password for andavane: 
Sorry, try again.
[sudo] password for andavane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  brscan
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 196748 files and directories currently installed.)
Removing brscan ...
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHLFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHMFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHminiFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLe': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLeFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory
dpkg: error processing brscan (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan
E: Sub-process /usr/bin/dpkg returned an error code (1)
andavane@andavane-vaayubuntu:~$ sudo apt-get remove /var/lib/brscan
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 
andavane@andavane-vaayubuntu:~$ 


---

