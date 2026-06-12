---
title: "[SOLVED] Googleearth gone from pkg mgr"
date: 2008-12-19
forum: General Help
---

### Post by spennyb on 2008-12-19
Hello all, Just re-installed my laptop with Ubuntu 8.10 and have noticed that google earth has gone from the pkg manager. I installed it from there not that long ago (In last month). When try to install via apt-get I see...

root@ebygum:~/Backup# apt-get install googleearth-4.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package googleearth-4.3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package googleearth-4.3 has no installation candidate

root@ebygum:~/Backup# apt-get install googleearth-4.3-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package googleearth-4.3-data is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package googleearth-4.3-data has no installation candidate


Has this been moved from the repository does anyone know ??. I know I can get it direct from google but it was easier via the pkg mgr.

Thanks in advance,
Spence.

---

### Post by Titan8990 on 2008-12-19
I am still using 7.10 and it's repositories but for 7.10 it is this:


sudo apt-get install googleearth-package



Use the following command to see the package name for your repositories:


apt-cache search googleearth

---

### Post by jflaker on 2008-12-19
It is still there.    I am using 8.10 and the package is called

googleearth-package

---

### Post by jrusso2 on 2008-12-19
I think google earth is in the mediabuntu repository make sure you have that enabled.

---

### Post by spennyb on 2008-12-19
Hi all, Thanks, tried installing that but that is...

root@ebygum:~# dpkg -l googleearth-package
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  googleearth-package       0.5.4                     utility to automatically build a Debian package of Google Earth


And contains...
root@ebygum:~# dpkg -L googleearth-package
/.
/usr
/usr/bin
/usr/bin/make-googleearth-package
/usr/share
/usr/share/doc
/usr/share/doc/googleearth-package
/usr/share/doc/googleearth-package/README.Debian
/usr/share/doc/googleearth-package/copyright
/usr/share/doc/googleearth-package/changelog.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/make-googleearth-package.1.gz


So not google earth, just docs. From old dpkg output it was called...

spencerb@ebygum:~/Backup$ grep googleearth ubuntu-files
googleearth-4.3					install
googleearth-4.3-data				install

---

### Post by Titan8990 on 2008-12-19
This appears to be the binary/script that will build google earth:

/usr/bin/make-googleearth-package

---

### Post by jerome1232 on 2008-12-19
```
apt-cache show googleearth
Package: googleearth
Version: 4.3.7284.3916-0medibuntu3
Architecture: all
Maintainer: Medibuntu Packaging Team <admin@lists.medibuntu.org>
Installed-Size: 96
Depends: googleearth-4.2 | googleearth-4.3
Homepage: http://earth.google.com/
Priority: extra
Section: non-free/net
Filename: pool/non-free/g/googleearth/googleearth_4.3.7284.3916-0medibuntu3_all.deb
Size: 24776
SHA256: 04aae7d9fa1e149e03877841e425deadcb5b5619fd2c170629c3c47b7e4cee9f
SHA1: 9d2096bf86952d4c1e91903a070ea0ae7d2b94e8
MD5sum: 558b964ede9bc1a1ffb9d53fd3e33cf2
Description: metapackage for Google Earth!
 The idea is simple. It's a globe that sits inside your PC. You point
 and zoom to anyplace on the planet that you want to explore.
 Satellite images and local facts zoom into view. Tap into Google
 search to show local points of interest and facts. Zoom to a
 specific address to check out an apartment or hotel. View driving
 directions and even fly along your route. We invite you to try it
 now.
 .
 NOTE: If you have an ATI graphic card using the proprietary (fglrx) driver,
 please read carefully /usr/share/doc/googleearth/README.Debian before
 reporting any bug.
 .
 This is in Medibuntu because of its non-free license.
 .
 This is a metapackage which allows to install Google Earth! 4.2 or
 Google Earth! 4.3.
```

Deffintly in the medibuntu repo, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by spennyb on 2008-12-19
Thx all

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

worked

---

