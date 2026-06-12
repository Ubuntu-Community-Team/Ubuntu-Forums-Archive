---
title: "PKI Client 5.00 install (for eToken Pro)"
date: 2009-07-29
forum: Desktop Environments
---

### Post by MasterOfTheHat on 2009-07-29
My company uses the Aladdin eToken Pro for authentication on VPN connections. The eToken requires a PKI client application on the client machine before the OS will even recognize it. The app and token work fine on XP, but I use Ubuntu on my laptop. Aladdin has offered a Linux version of the client, but only as a rpm. We convinced our internal IT guys to get us the rpms, and I've been trying to get it to work for a couple days.

To begin with, this is a HP Pavilion dv4-1435dx laptop running Jaunty 64-bit. 

- I started out by converting the .rpm to a .deb using alien:
```
sudo alien -d pkiclient-5.00.28-0.x86_64.rpm
```
- That worked fine and I got a nice little .deb
- Next, I ran the .deb to install the client:
```
sudo dpkg -i pkiclient_5.00.28-1_amd64.deb
```
- And it executed without any errors/issues. The pdf with the rpm said that there should be a launcher at Applications > eToken > Start eToken PKI Client, but that didn't exist. I figured that might be because I installed it from the deb instead of the rpm. I bounced the box, but it still wasn't there. No big deal...
- Install network manager so that I can configure a VPN connection to use the token:
```
sudo aptitude install network-manager-vpnc network-manager-openvpn
```
- Go to create the VPN connection and find nothing that looks obvious for using the token...
- I verified that computer is seeing the token when it's plugged in:
```
~$ lsusb
Bus 002 Device 003: ID 174f:1107 Syntek 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0529:0600 Aladdin Knowledge Systems eToken Pro 64k (4.2)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
- After some digging, I figured out that the eToken should also have a daemon running: eTSrv
- When I try to start the eTSrv daemon, it fails with the following:
```
~$ sudo /etc/init.d/eTSrv start
Starting eTSrv: /usr/bin/eTSrv: error while loading shared libraries: libpcsclite.so.1: cannot open shared object file: No such file or directory
Failed
```

I've found several posts for other uses of libpcsclite.so.* where people have had to create symlinks or modify the ld.so.conf file to tell the app where to look for the library, so I went looking for the file and found it in /lib. I've tried creating symlinks to /usr/lib, /usr/local/lib, etc and still get same results. The only time I've gotten anything other than the "cannot open shared object file" error was when I created a link to /usr/lib32:
```
:~$ sudo /etc/init.d/eTSrv start
Starting eTSrv: /usr/bin/eTSrv: error while loading shared libraries: libpcsclite.so.1: wrong ELF class: ELFCLASS64
Failed
```
I've looked at the eTSrv init script, but I can't figure out where any of it is looking for the libpcsclite.so.1 library, so I can't figure out what to modify to get the app to find it.

Any suggestions?

---

### Post by white_hat on 2009-09-08
try this [http://www.aladdin.ru/bitrix/redirect.php?event1=download&event2=eTokenPKIClientLinux50SP1_2009-08-18.zip&goto=/upload/iblock/178/etokenpkiclientlinux50sp1_2009-08-18.zip](http://www.aladdin.ru/bitrix/redirect.php?event1=download&event2=eTokenPKIClientLinux50SP1_2009-08-18.zip&goto=/upload/iblock/178/etokenpkiclientlinux50sp1_2009-08-18.zip)
works for me

---

### Post by MasterOfTheHat on 2009-09-08
Looks good, White_Hat, except that I'm running 64-bit Ubuntu, and the 64-bit .deb isn't included! Arrgh! Did you get this latest package from the vendor?

Thanks for the help, btw.

---

### Post by lgoulart on 2010-04-11
Hi MasterOfTheHat,

I've followed your steps on how to put the eToken Pro into use I got stuck exactly where you are.

The problem is that I'm a complete newbie in Linux and Ubuntu, but I really need this eToken to work to get rid of Windows for once and for all.

I'd like to know if you had any progress on that. Btw, I'm using Ubuntu 9.10.

Tks in advance.

---

### Post by rosi on 2010-05-03
> **MasterOfTheHat said:**
> Looks good, White_Hat, except that I'm running 64-bit Ubuntu, and the 64-bit .deb isn't included! Arrgh! Did you get this latest package from the vendor?

Thanks for the help, btw.

I've got same problem on 
Linux sirnb 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid

Any news ? Any idea to solve this problem ?

---

### Post by lgoulart on 2010-05-05
Hi all,

I've got a RPM file with the PKIClient 64 bits but I can't convert it with Alien to a .deb file.

When using this command line: sudo alien --scripts -k pkiclient-5.00.28-0.x86_64.rpm I got this response:

error: incorrect format: unknown tag
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: Compatibility levels before 5 are deprecated.
dh_installdirs
dh_installdirs: Compatibility levels before 5 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 5 are deprecated.
dh_installchangelogs
dh_installchangelogs: Compatibility levels before 5 are deprecated.
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/pkiclient
dh_compress
dh_compress: Compatibility levels before 5 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 5 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 5 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 5 are deprecated.
dpkg-shlibdeps: error: couldn't find library libpcsclite.so.1 needed by debian/pkiclient/usr/bin/eTSrv (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps -Tdebian/pkiclient.substvars debian/pkiclient/lib/libeToken.so.5.00 debian/pkiclient/lib/libeTokenUI.so.5.00 debian/pkiclient/lib64/libeToken.so.5.00 debian/pkiclient/usr/bin/etProps debian/pkiclient/usr/bin/eTSrv debian/pkiclient/usr/bin/PKIMonitor debian/pkiclient/usr/lib/eToken/bin/etOpenDialog debian/pkiclient/usr/lib/eToken/libetPropBasic.so debian/pkiclient/usr/lib/eToken/libMozilaStoreSync.so debian/pkiclient/usr/lib/eToken/libPhysicalDevices.so debian/pkiclient/usr/lib/eToken/libQtCore.so.4.2.3 debian/pkiclient/usr/lib/eToken/libQtGui.so.4.2.3 debian/pkiclient/usr/lib/eToken/libQtXml.so.4.2.3 debian/pkiclient/usr/lib/eToken/nss_tools/certutil debian/pkiclient/usr/lib/eToken/nss_tools/libfreebl3.so debian/pkiclient/usr/lib/eToken/nss_tools/libnspr4.so debian/pkiclient/usr/lib/eToken/nss_tools/libnss3.so debian/pkiclient/usr/lib/eToken/nss_tools/libplc4.so debian/pkiclient/usr/lib/eToken/nss_tools/libplds4.so debian/pkiclient/usr/lib/eToken/nss_tools/libsmime3.so debian/pkiclient/usr/lib/eToken/nss_tools/libsoftokn3.so debian/pkiclient/usr/lib/eToken/nss_tools/libssl3.so debian/pkiclient/usr/lib/eToken/nss_tools/modutil debian/pkiclient/usr/lib/eToken/plugins/imageformats/libqjpeg.so debian/pkiclient/usr/share/eToken/drivers/aks-ifdh.bundle/Contents/Linux/libAksIfdh.so.5.00 returned exit code 2
make: [binary-arch] Error 9 (ignored)
dh_gencontrol
dh_gencontrol: Compatibility levels before 5 are deprecated.
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_md5sums: Compatibility levels before 5 are deprecated.
dh_builddeb
dh_builddeb: Compatibility levels before 5 are deprecated.
dpkg-deb: control directory has bad permissions 700 (must be >=0755 and <=0775)
dpkg-deb: building package `pkiclient' in `../pkiclient_5.00.28-0_amd64.deb'.
dh_builddeb: dpkg-deb --build debian/pkiclient .. returned exit code 2
make: *** [binary-arch] Error 9
find: `pkiclient-5.00.28': No such file or directory

Any clues on how to solve this? Tks in advance.

---

### Post by rosi on 2010-05-06
Hi,
on ubuntu 9.10 is convert without problem, but after install pkiclient_5.00.28-1_amd64.deb I've got trouble with pcsclite
(~$ sudo /etc/init.d/eTSrv start
Starting eTSrv: /usr/bin/eTSrv: error while loading shared libraries: libpcsclite.so.1: cannot open shared object file: No such file or directory
Failed)


root@sirnb:~/etoken/RPM 64/RPM# ls -la
celkem 9684
drwxr-xr-x 2 root root    4096 2010-05-06 10:03 .
drwxr-xr-x 5 root root    4096 2010-05-06 10:00 ..
-rw-r--r-- 1 root root   85309 2010-05-06 10:03 log.txt
-rw-r--r-- 1 root root 9820232 2009-01-22 17:03 pkiclient-5.00.28-0.x86_64.rpm
root@sirnb:~/etoken/RPM 64/RPM# rm log.txt
root@sirnb:~/etoken/RPM 64/RPM# 






























root@sirnb:~/etoken/RPM 64/RPM# ls
pkiclient-5.00.28-0.x86_64.rpm
root@sirnb:~/etoken/RPM 64/RPM# alien -v pkiclient-5.00.28-0.x86_64.rpm 
	LANG=C rpm -qp --queryformat %{NAME} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qp --queryformat %{VERSION} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qp --queryformat %{RELEASE} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qp --queryformat %{ARCH} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qp --queryformat %{SUMMARY} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qp --queryformat %{DESCRIPTION} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qp --queryformat %{COPYRIGHT} pkiclient-5.00.28-0.x86_64.rpm
error: incorrect format: unknown tag
	LANG=C rpm -qp --queryformat %{PREFIXES} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qp --queryformat %{POSTIN} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qp --queryformat %{POSTUN} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qp --queryformat %{PREUN} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qp --queryformat %{PREIN} pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qcp pkiclient-5.00.28-0.x86_64.rpm
	rpm -qpi pkiclient-5.00.28-0.x86_64.rpm
	LANG=C rpm -qpl pkiclient-5.00.28-0.x86_64.rpm
Warning: Skipping conversion of scripts in package pkiclient: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
	mkdir pkiclient-5.00.28
	chmod 755 pkiclient-5.00.28
	rpm2cpio pkiclient-5.00.28-0.x86_64.rpm | (cd pkiclient-5.00.28; cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1
	chmod 755 pkiclient-5.00.28/./
	chmod 755 pkiclient-5.00.28/./lib64
	chmod 755 pkiclient-5.00.28/./var
	chmod 755 pkiclient-5.00.28/./var/cache
	chmod 755 pkiclient-5.00.28/./usr
	chmod 755 pkiclient-5.00.28/./usr/bin
	chmod 755 pkiclient-5.00.28/./usr/lib64
	chmod 755 pkiclient-5.00.28/./usr/share
	chmod 755 pkiclient-5.00.28/./usr/share/doc
	chmod 755 pkiclient-5.00.28/./usr/lib
	chmod 755 pkiclient-5.00.28/./etc
	chmod 755 pkiclient-5.00.28/./etc/rc.d
	chmod 755 pkiclient-5.00.28/./etc/rc.d/rc3.d
	chmod 755 pkiclient-5.00.28/./etc/rc.d/rc0.d
	chmod 755 pkiclient-5.00.28/./etc/rc.d/rc1.d
	chmod 755 pkiclient-5.00.28/./etc/rc.d/rc4.d
	chmod 755 pkiclient-5.00.28/./etc/rc.d/rc5.d
	chmod 755 pkiclient-5.00.28/./etc/rc.d/rc6.d
	chmod 755 pkiclient-5.00.28/./etc/init.d
	chmod 755 pkiclient-5.00.28/./etc/ld.so.conf.d
	chmod 755 pkiclient-5.00.28/./lib
	chown 0:0 pkiclient-5.00.28//etc/eToken.common.conf
	chmod 666 pkiclient-5.00.28//etc/eToken.common.conf
	chown 0:0 pkiclient-5.00.28//etc/eToken.conf
	chmod 644 pkiclient-5.00.28//etc/eToken.conf
	chown 0:0 pkiclient-5.00.28//etc/init.d/eTSrv
	chmod 755 pkiclient-5.00.28//etc/init.d/eTSrv
	chown 0:0 pkiclient-5.00.28//etc/ld.so.conf.d/wwwwetoken-ld.conf
	chmod 644 pkiclient-5.00.28//etc/ld.so.conf.d/wwwwetoken-ld.conf
	chown 0:0 pkiclient-5.00.28//lib/libeToken.so.5.00
	chmod 755 pkiclient-5.00.28//lib/libeToken.so.5.00
	chown 0:0 pkiclient-5.00.28//lib/libeTokenUI.so.5.00
	chmod 755 pkiclient-5.00.28//lib/libeTokenUI.so.5.00
	chown 0:0 pkiclient-5.00.28//lib64/libeToken.so.5.00
	chmod 755 pkiclient-5.00.28//lib64/libeToken.so.5.00
	chown 0:0 pkiclient-5.00.28//usr/bin/PKIMonitor
	chmod 755 pkiclient-5.00.28//usr/bin/PKIMonitor
	chown 0:0 pkiclient-5.00.28//usr/bin/eTSrv
	chmod 755 pkiclient-5.00.28//usr/bin/eTSrv
	chown 0:0 pkiclient-5.00.28//usr/bin/etProps
	chmod 755 pkiclient-5.00.28//usr/bin/etProps
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken
	chmod 755 pkiclient-5.00.28//usr/lib/eToken
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/bin
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/bin
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/bin/etOpenDialog
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/bin/etOpenDialog
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/libMozilaStoreSync.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/libMozilaStoreSync.so
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/libPhysicalDevices.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/libPhysicalDevices.so
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/libQtCore.so.4.2.3
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/libQtCore.so.4.2.3
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/libQtGui.so.4.2.3
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/libQtGui.so.4.2.3
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/libQtXml.so.4.2.3
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/libQtXml.so.4.2.3
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/libetPropBasic.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/libetPropBasic.so
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/nss_tools
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/nss_tools
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/nss_tools/certutil
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/nss_tools/certutil
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libfreebl3.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libfreebl3.so
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libnspr4.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libnspr4.so
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libnss3.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libnss3.so
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libplc4.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libplc4.so
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libplds4.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libplds4.so
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libsmime3.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libsmime3.so
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libsoftokn3.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libsoftokn3.so
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libssl3.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/nss_tools/libssl3.so
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/nss_tools/modutil
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/nss_tools/modutil
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/plugins
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/plugins
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/plugins/imageformats
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/plugins/imageformats
	chown 0:0 pkiclient-5.00.28//usr/lib/eToken/plugins/imageformats/libqjpeg.so
	chmod 755 pkiclient-5.00.28//usr/lib/eToken/plugins/imageformats/libqjpeg.so
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken
	chmod 755 pkiclient-5.00.28//usr/share/doc/eToken
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/LICENSE.txt
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/LICENSE.txt
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help
	chmod 755 pkiclient-5.00.28//usr/share/doc/eToken/help
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/about.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/about.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/adding_an_etoken_virtual_or_etoken_rescue.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/adding_an_etoken_virtual_or_etoken_rescue.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/advanced_view1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/advanced_view1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/advanced_view_functions.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/advanced_view_functions.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/aladdin-white.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/aladdin-white.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/attached_etokens.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/attached_etokens.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/autoconnecting_etoken_virtual.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/autoconnecting_etoken_virtual.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/bottom.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/bottom.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/changing_an_etoken_password.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/changing_an_etoken_password.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/changing_the_etoken_initialization_key.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/changing_the_etoken_initialization_key.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/changing_the_etoken_password1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/changing_the_etoken_password1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/clearing_a_default_certificate.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/clearing_a_default_certificate.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/clearing_an_etoken.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/clearing_an_etoken.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/configuring_advanced_initialization_settings.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/configuring_advanced_initialization_settings.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/copying_etoken_information_to_the_clipboard.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/copying_etoken_information_to_the_clipboard.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/copying_user_certificates_to_a_local_store.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/copying_user_certificates_to_a_local_store.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/copyrights_and_trademarks.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/copyrights_and_trademarks.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/cshdat_robohelp.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/cshdat_robohelp.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/cshdat_webhelp.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/cshdat_webhelp.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/deleting_a_certificate.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/deleting_a_certificate.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/disconnecting_or_deleting_an_etoken_virtual_or_etoken_rescue.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/disconnecting_or_deleting_an_etoken_virtual_or_etoken_rescue.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/ehelp.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/ehelp.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/ehlpdhtm.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/ehlpdhtm.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/enabling_ca_certificate_management.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/enabling_ca_certificate_management.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/enabling_configuration_after_initialization.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/enabling_configuration_after_initialization.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/enabling_configuration_by_administrator_or_user.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/enabling_configuration_by_administrator_or_user.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/enabling_single_sign-on_mode.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/enabling_single_sign-on_mode.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken properties.log
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken properties.log
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_device_icons.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_device_icons.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_initialization.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_initialization.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_management.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_management.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_pki_client_properties_main_screen_toolbar.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_pki_client_properties_main_screen_toolbar.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_pki_client_tray_icon.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_pki_client_tray_icon.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_pki_client_tray_icon_functions.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_pki_client_tray_icon_functions.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_pki_client_user_interface.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_pki_client_user_interface.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_properties.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_properties.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_properties_csh.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_properties_csh.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_properties_rhc.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_properties_rhc.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_settings.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_settings.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_virtual.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/etoken_virtual.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/exporting_a_certificate.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/exporting_a_certificate.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/fcc_compliance.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/fcc_compliance.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/generating_a_one_time_password_(otp).htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/generating_a_one_time_password_(otp).htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/header.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/header.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/hiding_and_unhiding_the_etoken_properties_tray_menu.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/hiding_and_unhiding_the_etoken_properties_tray_menu.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image1.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image1.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image1.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image1.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image10.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image10.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image11.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image11.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image11.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image11.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image12.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image12.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image12.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image12.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image13.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image13.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image13.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image13.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image14.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image14.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image14.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image14.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image15.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image15.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image15.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image15.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image16.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image16.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image16.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image16.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image17.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image17.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image17.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image17.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image18.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image18.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image18.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image18.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image19.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image19.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image19.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image19.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image2.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image2.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image2.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image2.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image20.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image20.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image21.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image21.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image21.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image21.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image22.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image22.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image23.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image23.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image23.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image23.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image24.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image24.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image24.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image24.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image25.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image25.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image25.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image25.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image26.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image26.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image26.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image26.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image27.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image27.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image27.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image27.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image28.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image28.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image29.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image29.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image29.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image29.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image3.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image3.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image3.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image3.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image30.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image30.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image31.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image31.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image32.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image32.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image32.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image32.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image33.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image33.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image33.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image33.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image34.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image34.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image35.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image35.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image36.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image36.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image36.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image36.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image37.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image37.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image38.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image38.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image38.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image38.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image39.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image39.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image4.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image4.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image4.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image4.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image40.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image40.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image40.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image40.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image41.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image41.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image42.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image42.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image42.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image42.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image43.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image43.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image44.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image44.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image45.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image45.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image46.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image46.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image48.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image48.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image5.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image5.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image5.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image5.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image50.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image50.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image51.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image51.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image53.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image53.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image54.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image54.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image55.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image55.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image56.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image56.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image58.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image58.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image59.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image59.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image6.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image6.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image60.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image60.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image61.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image61.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image62.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image62.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image64.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image64.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image65.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image65.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image66.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image66.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image67.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image67.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image68.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image68.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image69.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image69.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image7.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image7.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image7.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image7.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image70.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image70.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image72.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image72.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image73.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image73.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image8.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image8.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image9.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image9.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/image9.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/image9.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/importing_a_certificate_onto_an_etoken.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/importing_a_certificate_onto_an_etoken.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/initializing_an_etoken.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/initializing_an_etoken.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/introduction.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/introduction.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/launching_the_etoken_ng-flash_partition_application.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/launching_the_etoken_ng-flash_partition_application.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/launching_the_etoken_pki_client_tray_menu.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/launching_the_etoken_pki_client_tray_menu.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/logging_on_to_an_etoken.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/logging_on_to_an_etoken.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/logging_on_to_an_etoken_as_a_user.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/logging_on_to_an_etoken_as_a_user.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/logging_on_to_an_etoken_as_an_administrator.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/logging_on_to_an_etoken_as_an_administrator.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/managing_readers1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/managing_readers1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/new_features.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/new_features.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/opening_etoken_pki_client_settings.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/opening_etoken_pki_client_settings.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/overview.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/overview.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/overview_of_etoken_initialization.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/overview_of_etoken_initialization.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/overview_of_etoken_pki_client_user_interface.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/overview_of_etoken_pki_client_user_interface.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/overview_of_etoken_virtual_and_etoken_rescue.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/overview_of_etoken_virtual_and_etoken_rescue.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/patent_protection.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/patent_protection.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/pki_client_settings1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/pki_client_settings1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/pki_client_settings2.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/pki_client_settings2.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/renaming_an_etoken.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/renaming_an_etoken.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/robohhre.lng
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/robohhre.lng
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/selecting_the_active_etoken.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/selecting_the_active_etoken.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/setting_a_certificate_as_default_or_auxiliary.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/setting_a_certificate_as_default_or_auxiliary.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/setting_etoken_password_quality.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/setting_etoken_password_quality.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/setting_etoken_pki_client_settings_password_quality.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/setting_etoken_pki_client_settings_password_quality.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/setting_private_data_caching_mode.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/setting_private_data_caching_mode.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/setting_rsa_key_second_authentication_mode.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/setting_rsa_key_second_authentication_mode.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/settings1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/settings1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/simple_view1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/simple_view1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/simple_view_functions.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/simple_view_functions.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/synchronizing_passwords.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/synchronizing_passwords.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/tms_sdk.css
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/tms_sdk.css
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/tms_sdk_ns.css
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/tms_sdk_ns.css
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/tokens_node.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/tokens_node.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/unlocking_an_etoken.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/unlocking_an_etoken.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/unlocking_an_etoken_using_challenge_-_response.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/unlocking_an_etoken_using_challenge_-_response.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/unlocking_an_etoken_using_set_user_password.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/unlocking_an_etoken_using_set_user_password.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/unlocking_an_etoken_virtual_etoken_rescue_.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/unlocking_an_etoken_virtual_etoken_rescue_.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/user_certificates1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/user_certificates1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/using_an_etoken_virtual_etoken_rescue_to_replace_a_lost_etoken.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/using_an_etoken_virtual_etoken_rescue_to_replace_a_lost_etoken.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/viewing_etoken_information1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/viewing_etoken_information1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/webhelp.cab
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/webhelp.cab
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/webhelp.jar
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/webhelp.jar
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whcsh_home.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whcsh_home.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whcshdata.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whcshdata.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata
	chmod 755 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whftdata.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whftdata.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whftdata0.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whftdata0.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfts.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfts.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfts.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfts.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfwdata.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfwdata.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfwdata0.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfwdata0.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfwdata1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfwdata1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfwdata2.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfwdata2.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfwdata3.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whfwdata3.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whgdata.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whgdata.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whglo.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whglo.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whglo.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whglo.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whidata.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whidata.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whidx.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whidx.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whidx.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whidx.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whtdata.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whtdata.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whtdata0.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whtdata0.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whtoc.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whtoc.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whtoc.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whdata/whtoc.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whestart.ico
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whestart.ico
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whfbody.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whfbody.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whfdhtml.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whfdhtml.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whfform.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whfform.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whfhost.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whfhost.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whform.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whform.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whframes.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whframes.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgbody.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgbody.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata
	chmod 755 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whexpbar.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whexpbar.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf0.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf0.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf10.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf10.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf2.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf2.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf3.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf3.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf4.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf4.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf5.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf5.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf6.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf6.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf7.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf7.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf8.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf8.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf9.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstf9.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl0.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl0.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl10.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl10.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl11.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl11.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl12.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl12.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl13.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl13.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl14.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl14.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl15.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl15.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl16.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl16.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl17.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl17.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl18.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl18.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl19.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl19.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl2.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl2.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl20.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl20.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl21.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl21.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl3.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl3.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl4.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl4.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl5.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl5.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl6.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl6.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl7.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl7.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl8.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl8.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl9.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstfl9.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstg0.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstg0.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlsti0.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlsti0.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt0.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt0.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt1.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt1.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt10.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt10.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt11.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt11.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt12.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt12.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt13.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt13.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt14.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt14.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt15.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt15.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt16.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt16.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt2.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt2.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt3.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt3.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt4.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt4.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt5.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt5.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt6.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt6.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt7.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt7.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt8.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt8.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt9.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whlstt9.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvf30.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvf30.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvf31.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvf31.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvf32.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvf32.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvf33.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvf33.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvl31.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvl31.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvl32.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvl32.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvl33.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvl33.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvp30.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvp30.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvp31.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvp31.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvp32.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvp32.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvp33.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvp33.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvt30.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvt30.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvt31.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvt31.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvt32.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvt32.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvt33.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdata/whnvt33.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdef.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdef.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdhtml.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whgdhtml.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whghost.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whghost.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whhost.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whhost.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whibody.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whibody.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whidhtml.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whidhtml.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whiform.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whiform.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whihost.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whihost.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whlang.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whlang.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whmozemu.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whmozemu.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whmsg.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whmsg.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whnjs.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whnjs.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whphost.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whphost.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whproj.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whproj.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whproj.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whproj.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whproj.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whproj.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whproxy.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whproxy.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whres.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whres.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whrstart.ico
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whrstart.ico
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_banner.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_banner.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_blank.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_blank.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_frmset01.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_frmset01.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_frmset010.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_frmset010.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_homepage.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_homepage.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_info.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_info.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_mbars.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_mbars.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_papplet.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_papplet.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_pdhtml.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_pdhtml.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_pickup.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_pickup.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_plist.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_plist.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_tbars.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_tbars.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_tw.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whskin_tw.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whst_topics.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whst_topics.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whstart.ico
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whstart.ico
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whstart.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whstart.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whstub.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whstub.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abge.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abge.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abgi.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abgi.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abgw.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abgw.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abte.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abte.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abti.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abti.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abtw.jpg
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_abtw.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_fts_h.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_fts_h.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_fts_n.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_fts_n.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_glo_h.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_glo_h.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_glo_n.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_glo_n.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_go.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_go.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_hide.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_hide.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_idx_h.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_idx_h.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_idx_n.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_idx_n.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_logo1.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_logo1.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_logo2.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_logo2.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_next.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_next.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_next_g.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_next_g.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_prev.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_prev.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_prev_g.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_prev_g.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_spac.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_spac.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_sync.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_sync.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab0.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab0.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab1.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab1.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab2.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab2.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab3.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab3.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab4.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab4.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab5.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab5.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab6.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab6.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab7.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab7.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab8.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_tab8.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc1.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc1.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc2.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc2.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc3.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc3.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc4.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc4.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc_h.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc_h.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc_n.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_toc_n.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_ws.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_ws.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_ws_g.gif
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/wht_ws_g.gif
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whtbar.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whtbar.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whtdhtml.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whtdhtml.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whthost.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whthost.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whtopic.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whtopic.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whutils.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whutils.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whver.js
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whver.js
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata
	chmod 755 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whftdata0.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whftdata0.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whfts.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whfts.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whfwdata0.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whfwdata0.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whfwdata1.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whfwdata1.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whfwdata2.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whfwdata2.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whfwdata3.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whfwdata3.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whglo.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whglo.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whidx.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whidx.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whtdata0.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whtdata0.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whtoc.xml
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/whxdata/whtoc.xml
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/help/working_with_emulated_etoken_virtual.htm
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/help/working_with_emulated_etoken_virtual.htm
	chown 0:0 pkiclient-5.00.28//usr/share/doc/eToken/version
	chmod 644 pkiclient-5.00.28//usr/share/doc/eToken/version
	chown 0:0 pkiclient-5.00.28//usr/share/eToken
	chmod 755 pkiclient-5.00.28//usr/share/eToken
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages
	chmod 755 pkiclient-5.00.28//usr/share/eToken/LogoImages
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/CommonUIChangeAdminPasswordBackground.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/CommonUIChangeAdminPasswordBackground.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/CommonUIChangePasswordBackground.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/CommonUIChangePasswordBackground.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/CommonUILogonBackground.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/CommonUILogonBackground.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/CommonUISetPasswordBackground.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/CommonUISetPasswordBackground.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/MainetPropsWindowBottomBarLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/MainetPropsWindowBottomBarLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/MainetPropsWindowUpperBarLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/MainetPropsWindowUpperBarLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/aladdinWatermarkBackground.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/aladdinWatermarkBackground.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/eTokenUISelectTokenDialogHeader.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/eTokenUISelectTokenDialogHeader.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsAboutLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsAboutLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsAdvancedBottomBarLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsAdvancedBottomBarLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsAdvancedUpperBarLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsAdvancedUpperBarLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsCertStoreUpperBarLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsCertStoreUpperBarLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsHelpLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsHelpLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsImportCertLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsImportCertLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsInitKeyDialogLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsInitKeyDialogLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsInitializationProcessDialogLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsInitializationProcessDialogLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsInsertPasswordDialogLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsInsertPasswordDialogLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsReadersManagementDialogLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsReadersManagementDialogLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsRenameTokenDialogLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsRenameTokenDialogLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsTokenInfoDialogLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsTokenInfoDialogLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsUnblockTokenDialogLogo.jpg
	chmod 644 pkiclient-5.00.28//usr/share/eToken/LogoImages/etPropsUnblockTokenDialogLogo.jpg
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/drivers
	chmod 755 pkiclient-5.00.28//usr/share/eToken/drivers
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle
	chmod 755 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle/Contents
	chmod 755 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle/Contents
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle/Contents/Info.plist
	chmod 644 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle/Contents/Info.plist
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle/Contents/Linux
	chmod 755 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle/Contents/Linux
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle/Contents/Linux/libAksIfdh.so.5.00
	chmod 755 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle/Contents/Linux/libAksIfdh.so.5.00
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle/Contents/Linux/readme.txt
	chmod 644 pkiclient-5.00.28//usr/share/eToken/drivers/aks-ifdh.bundle/Contents/Linux/readme.txt
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages
	chmod 755 pkiclient-5.00.28//usr/share/eToken/languages
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_De.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_De.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_En.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_En.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Es.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Es.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Fr.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Fr.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Frca.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Frca.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_It.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_It.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Jp.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Jp.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Ko.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Ko.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Pl.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Pl.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Pt.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Pt.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Ru.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Ru.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Th.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Th.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Zh.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PKIMonitor_Zh.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_De.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_De.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_En.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_En.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Es.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Es.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Fr.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Fr.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Frca.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Frca.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_It.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_It.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Jp.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Jp.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Ko.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Ko.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Pl.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Pl.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Pt.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Pt.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Ru.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Ru.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Th.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Th.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Zh.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/PhysicalDevices_Zh.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_De.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_De.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_En.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_En.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Es.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Es.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Fr.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Fr.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Frca.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Frca.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_It.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_It.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Jp.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Jp.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Ko.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Ko.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Pl.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Pl.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Pt.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Pt.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Ru.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Ru.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Th.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Th.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Zh.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/RegistereTokenVirtual_Zh.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_De.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_De.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_En.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_En.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Es.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Es.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Fr.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Fr.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Frca.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Frca.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_It.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_It.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Jp.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Jp.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Ko.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Ko.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Pl.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Pl.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Pt.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Pt.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Ru.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Ru.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Th.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Th.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Zh.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/StoreSync_Zh.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_De.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_De.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_En.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_En.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Es.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Es.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Fr.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Fr.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Frca.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Frca.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_It.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_It.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Jp.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Jp.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Ko.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Ko.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_PL.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_PL.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Pt.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Pt.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Ru.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Ru.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Th.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Th.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Zh.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/commonUI_Zh.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_De.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_De.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_En.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_En.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Es.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Es.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Fr.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Fr.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Frca.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Frca.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_It.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_It.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Jp.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Jp.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Ko.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Ko.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Pl.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Pl.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Pt.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Pt.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Ru.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Ru.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Th.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Th.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Zh.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/eTokenUI_Zh.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_De.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_De.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_En.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_En.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Es.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Es.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Fr.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Fr.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Frca.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Frca.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_It.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_It.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Jp.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Jp.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Ko.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Ko.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Pl.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Pl.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Pt.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Pt.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Ru.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Ru.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Th.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Th.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Zh.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etPropBasic_Zh.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_De.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_De.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_En.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_En.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Es.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Es.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Fr.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Fr.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Frca.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Frca.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_It.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_It.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Jp.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Jp.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Ko.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Ko.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Pl.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Pl.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Pt.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Pt.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Ru.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Ru.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Th.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Th.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Zh.qm
	chmod 644 pkiclient-5.00.28//usr/share/eToken/languages/etProps_Zh.qm
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/shortcuts
	chmod 755 pkiclient-5.00.28//usr/share/eToken/shortcuts
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/shortcuts/PKIMonitor.desktop
	chmod 644 pkiclient-5.00.28//usr/share/eToken/shortcuts/PKIMonitor.desktop
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/shortcuts/eToken-PKI-Client.directory
	chmod 644 pkiclient-5.00.28//usr/share/eToken/shortcuts/eToken-PKI-Client.directory
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/shortcuts/eToken.directory
	chmod 644 pkiclient-5.00.28//usr/share/eToken/shortcuts/eToken.directory
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/shortcuts/eToken.menu
	chmod 644 pkiclient-5.00.28//usr/share/eToken/shortcuts/eToken.menu
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/shortcuts/etProps.desktop
	chmod 644 pkiclient-5.00.28//usr/share/eToken/shortcuts/etProps.desktop
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/shortcuts/icons
	chmod 755 pkiclient-5.00.28//usr/share/eToken/shortcuts/icons
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/shortcuts/icons/PKIMonitor.png
	chmod 644 pkiclient-5.00.28//usr/share/eToken/shortcuts/icons/PKIMonitor.png
	chown 0:0 pkiclient-5.00.28//usr/share/eToken/shortcuts/icons/etProps.png
	chmod 644 pkiclient-5.00.28//usr/share/eToken/shortcuts/icons/etProps.png
	chown 0:0 pkiclient-5.00.28//var/cache/eToken
	chmod 777 pkiclient-5.00.28//var/cache/eToken
	mkdir pkiclient-5.00.28/debian
	hostname
	date -R
	hostname
	date -R
	chmod 755 pkiclient-5.00.28/debian/rules
	debian/rules binary 2>&1
pkiclient_5.00.28-1_amd64.deb generated
	find pkiclient-5.00.28 -type d -exec chmod 755 {} ;
	rm -rf pkiclient-5.00.28
root@sirnb:~/etoken/RPM 64/RPM# 
root@sirnb:~/etoken/RPM 64/RPM# ls -la
celkem 19136
drwxr-xr-x 2 root root    4096 2010-05-06 10:03 .
drwxr-xr-x 5 root root    4096 2010-05-06 10:00 ..
-rw-r--r-- 1 root root 9820232 2009-01-22 17:03 pkiclient-5.00.28-0.x86_64.rpm
-rw-r--r-- 1 root root 9762492 2010-05-06 10:03 pkiclient_5.00.28-1_amd64.deb
root@sirnb:~/etoken/RPM 64/RPM# 

I put pkiclient_5.00.28-1_amd64.deb to:
[http://www.uloz.to/4746697/pkiclient-5.00.28-1-amd64.deb](http://www.uloz.to/4746697/pkiclient-5.00.28-1-amd64.deb) so, this package not solve problem with pcsclite

---

### Post by Ksperis on 2010-05-06
Hello,


I have the same problem.
(deb package create with alien from pkiclient-5.00.28-0.x86_64.rpm)

eTSrv and etProps working for me when I remove 64bit library of eToken and overwrite the 32bit libraries of  pcsclite:

```

alien -g ../pkiclient-5.00.28-0.x86_64.rpm
cd pkiclient-5.00.28
rm lib64/libeToken.so.5*
sudo debian/rules binary
sudo dpkg -i ../pkiclient_5.00.28-1_amd64.deb

``````

wget http://fr.archive.ubuntu.com/ubuntu/pool/main/p/pcsc-lite/libpcsclite1_1.5.3-1ubuntu4_i386.deb
sudo dpkg -i --force-all libpcsclite1_1.5.3-1ubuntu4_i386.deb

```But I can't add the PKCS#11 module in Firefox (/usr/lib/libeTPkcs11.so)

```

ls -l /usr/lib/libeTPkcs11.so
lrwxrwxrwx 1 barbe barbe 26 2010-05-06 11:35 /usr/lib/libeTPkcs11.so -> ../../lib64/libeToken.so.5

file /lib64/libeToken.so.5.00
/lib64/libeToken.so.5.00: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, not stripped

```Any idea ?

---

### Post by Ksperis on 2010-05-06
It's working for me :
- I can use the PKCS#11 module   (with 64bit lib)
- eTSrv and etProps working   (with 32bit lib)

```

sudo alien -g ../pkiclient-5.00.28-0.x86_64.rpm
cd pkiclient-5.00.28
sudo mkdir lib32
sudo mv lib/libeToken.so.5* lib32/
sudo debian/rules binary
sudo dpkg -i ../pkiclient_5.00.28-1_amd64.deb
cd ..

wget http://fr.archive.ubuntu.com/ubuntu/pool/main/p/pcsc-lite/libpcsclite1_1.5.3-1ubuntu4_i386.deb
dpkg -x libpcsclite1_1.5.3-1ubuntu4_i386.deb libpcsclite1_32
cd libpcsclite1_32
sudo mv lib/* /lib32/

```

---

### Post by rosi on 2010-05-06
Not working for me. When I run etProps, I can't see eToken.
I don't understand what you mean with the: 
cd libpcsclite1_32
sudo mv lib/* /lib32/
I'm run mc and open libpcsclite1_1.5.3-1ubuntu4_i386.deb
and copy libpcsclite1_1.5.3-1ubuntu4_i386.deb/lib/* to /lib32/

---

### Post by rosi on 2010-05-06
Can you past me your deb file ?

---

### Post by Ksperis on 2010-05-06
> **rosi said:**
> 
I don't understand what you mean with the: 
cd libpcsclite1_32


[COLOR=#000000]Forgot :
[/COLOR]
```

dpkg -x libpcsclite1_1.5.3-1ubuntu4_i386.deb libpcsclite1_32

```> **rosi said:**
> 
sudo mv lib/* /lib32/
I'm run mc and open libpcsclite1_1.5.3-1ubuntu4_i386.deb
and copy libpcsclite1_1.5.3-1ubuntu4_i386.deb/lib/* to /lib32/

Do you have errors ?

---

### Post by rosi on 2010-05-07
Don't remember to install openct
sudo aptitude install libopenct1 libopenctl0 openct

---

### Post by warpitaly on 2011-05-04
> **Ksperis said:**
> 
Do you have errors ?


Hi! My installation fails claiming that it is unable to open 
"/lib64/libeToken.so.5.00.dpkg-new".

Any hint?

---

### Post by s3a on 2011-05-04
I didn't read everything so sorry if I am saying something dumb but if the problem is needing to get that 32 bit deb working then:

sudo dpkg -i --force architecture *.deb

---

