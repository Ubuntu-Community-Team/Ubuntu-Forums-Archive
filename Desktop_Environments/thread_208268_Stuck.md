---
title: "Stuck"
date: 2006-07-03
forum: Desktop Environments
---

### Post by artux on 2006-07-03
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

I did some commands from this page. The consequence was 3 hours of noob time to recover Xwindows.

I thought that this code:
> sudo dpkg -i *.deb
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx-kernel
sudo depmod

was a continuation for Dapper, but it seems that it is for Breezy.

**Is there a ware to recover any loss made by this code?**

Now I am trying to install the .Run ATI shell script given by ATI by going through the steps provided but here is what I receive:

[COLOR="Red"]rtux@rtuxDesk:~/install_files/ati driver installer$ sudo fakeroot sh ./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.26.18..................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/dapper
cp: cannot stat `/home/rtux/install_files/ati': No such file or directory
cp: cannot stat `driver': No such file or directory
cp: cannot stat `installer/fglrx-install/x690/*': No such file or directorycp: cannot stat `/home/rtux/install_files/ati': No such file or directory
cp: cannot stat `driver': No such file or directory
cp: cannot stat `installer/fglrx-install/arch/x86/*': No such file or directory
cp: cannot stat `/home/rtux/install_files/ati': No such file or directory
cp: cannot stat `driver': No such file or directory
cp: cannot stat `installer/fglrx-install/common/*': No such file or directory
chmod: cannot access `/home/rtux/install_files/ati': No such file or directory
chmod: cannot access `driver': No such file or directory
chmod: cannot access `installer/fglrx-install/packages/Ubuntu': No such file or directory
cp: cannot stat `/home/rtux/install_files/ati': No such file or directory
cp: cannot stat `driver': No such file or directory
cp: cannot stat `installer/fglrx-install/packages/Ubuntu/debian': No such file or directory
./packages/Ubuntu/ati-packager.sh: line 97: [: too many arguments
cp: cannot stat `/home/rtux/install_files/ati': No such file or directory
cp: cannot stat `driver': No such file or directory
cp: cannot stat `installer/fglrx-install/packages/Ubuntu/module': No such file or directory
./packages/Ubuntu/ati-packager.sh: line 33: /tmp/fglrx.fzWFQf/debian/changelog: No such file or directory
./packages/Ubuntu/ati-packager.sh: line 35: /tmp/fglrx.fzWFQf/debian/changelog: No such file or directory
./packages/Ubuntu/ati-packager.sh: line 37: /tmp/fglrx.fzWFQf/debian/changelog: No such file or directory
/tmp/fglrx.fzWFQf ~/install_files/ati driver installer/fglrx-install
Package build failed!
Package build utility output:
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is
~/install_files/ati driver installer/fglrx-install
Removing temporary directory: fglrx-install
[/COLOR]


**So what can I do to make it work?**

---

