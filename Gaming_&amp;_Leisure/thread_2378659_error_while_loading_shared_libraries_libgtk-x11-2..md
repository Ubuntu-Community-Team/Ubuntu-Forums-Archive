---
title: "error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object"
date: 2017-11-25
forum: Gaming &amp; Leisure
---

### Post by spaceman1980 on 2017-11-25
Hi everyone,
I'm running 17.10 and am trying to install America's Army 2.5 from Sourceforge. When I attempt to run the executable in the folder, I get the following message:
```
error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```
I believe that this is because I don't have the 32-bit gtk2.0 packages installed, but only the 64-bit ones. (The libgtk-x11-2.0.so.0 file is there). However, attempting to install the packages for the i386 architecture gives me this:
```
sudo apt insall libgtk2.0-0:i386
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Starting pkgProblemResolver with broken count: 1
Starting 2 pkgProblemResolver with broken count: 1
Investigating (0) libpangoft2-1.0-0 [ i386 ] < none -> 1.38.1-1 > ( libs )
Broken libpangoft2-1.0-0:i386 Depends on libharfbuzz0b [ i386 ] < none -> 1.0.1-1ubuntu0.1 > ( libs ) (>= 0.9.30)
  Considering libharfbuzz0b:i386 0 as a solution to libpangoft2-1.0-0:i386 1
  Holding Back libpangoft2-1.0-0:i386 rather than change libharfbuzz0b:i386
Investigating (0) libpangocairo-1.0-0 [ i386 ] < none -> 1.38.1-1 > ( libs )
Broken libpangocairo-1.0-0:i386 Depends on libpangoft2-1.0-0 [ i386 ] < none -> 1.38.1-1 > ( libs ) (>= 1.28.1)
  Considering libpangoft2-1.0-0:i386 1 as a solution to libpangocairo-1.0-0:i386 0
  Holding Back libpangocairo-1.0-0:i386 rather than change libpangoft2-1.0-0:i386
Investigating (1) libgtk2.0-0 [ i386 ] < none -> 2.24.30-1ubuntu1.16.04.2 > ( libs )
Broken libgtk2.0-0:i386 Depends on libpangocairo-1.0-0 [ i386 ] < none -> 1.38.1-1 > ( libs ) (>= 1.28.3)
  Considering libpangocairo-1.0-0:i386 0 as a solution to libgtk2.0-0:i386 9999
    Reinst Failed because of libharfbuzz0b:i386
    Reinst Failed because of libpangoft2-1.0-0:i386
Broken libgtk2.0-0:i386 Depends on libpangoft2-1.0-0 [ i386 ] < none -> 1.38.1-1 > ( libs ) (>= 1.28.3)
  Considering libpangoft2-1.0-0:i386 1 as a solution to libgtk2.0-0:i386 9999
Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgtk2.0-0:i386 : Depends: libpangocairo-1.0-0:i386 (>= 1.28.3) but it is not going to be installed
                    Depends: libpangoft2-1.0-0:i386 (>= 1.28.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I checked to see what my held packages are, and there are none. I have searched the internet quite a bit and still haven't found an answer. What do you guys think I should do? Thanks!

---

### Post by mc4man on 2017-11-25
Generally this would occur if there is a version mismatch between the amd64 & i386 versions of same packages, they must match exactly.
That can happen if security, updates repos  were enabled but aren't  now or vice-versa or if proposed was used at some point.

I'd  install aptitude & try installing with it. After first attempt q (quit) & read thru, see if it tells you why
sudo aptitude install libgtk2.0-0:i386

---

### Post by spaceman1980 on 2017-11-25
Thanks so much for the reply. I got this:
The following NEW packages will be installed:
  libatk1.0-0:i386{a} libavahi-client3:i386{a} libavahi-common-data:i386{a} libavahi-common3:i386{a} libcairo2:i386{a} libcomerr2:i386{a} libcups2:i386{a} 
  libdatrie1:i386{a} libdbus-1-3:i386{a} libfontconfig1:i386{a} libfreetype6:i386{a} libgcrypt20:i386{a} libgdk-pixbuf2.0-0:i386{a} libglib2.0-0:i386{a} 
  libgmp10:i386{a} libgnutls30:i386{a} libgpg-error0:i386{a} libgraphite2-3:i386{a} libgssapi-krb5-2:i386{a} libgtk2.0-0:i386 libharfbuzz0b:i386{ab} 
  libhogweed4:i386{a} libidn11:i386{a} libjbig0:i386{a} libjpeg-turbo8:i386{a} libjpeg8:i386{a} libk5crypto3:i386{a} libkeyutils1:i386{a} libkrb5-3:i386{a} 
  libkrb5support0:i386{a} liblzma5:i386{a} libnettle6:i386{a} libp11-kit0:i386{a} libpango-1.0-0:i386{a} libpangocairo-1.0-0:i386{a} libpangoft2-1.0-0:i386{a} 
  libpcre3:i386{a} libpixman-1-0:i386{a} libpng12-0:i386{a} libselinux1:i386{a} libsystemd0:i386{a} libtasn1-6:i386{a} libthai0:i386{a} libtiff5:i386{a} 
  libxcb-render0:i386{a} libxcb-shm0:i386{a} libxcomposite1:i386{a} libxcursor1:i386{a} libxi6:i386{a} libxrandr2:i386{a} libxrender1:i386{a} 
0 packages upgraded, 51 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,940 kB of archives. After unpacking 29.0 MB will be used.
The following packages have unmet dependencies:
 libharfbuzz0b : Breaks: libharfbuzz0b:i386 (!= 1.4.6-0neon+16.04+xenial+build3) but 1.0.1-1ubuntu0.1 is to be installed.
 libharfbuzz0b:i386 : Breaks: libharfbuzz0b (!= 1.0.1-1ubuntu0.1) but 1.4.6-0neon+16.04+xenial+build3 is installed.
open: 516; closed: 238; defer: 490; conflict: 645                                                                                                                        oThe following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libgtk2.0-0:i386 [Not Installed]                   
2)     libharfbuzz0b:i386 [Not Installed]                 
3)     libpangocairo-1.0-0:i386 [Not Installed]           
4)     libpangoft2-1.0-0:i386 [Not Installed]             

I don't completely understand the solution its giving me. Should I accept the solution?

---

### Post by mc4man on 2017-11-25
the issue is that the available (or already installed) libharfbuzz0b:i386 is  1.4.6-0neon+16.04+xenial+build3 which searches out as from some KDE Neon Dev stable repo

Post
```
apt policy libharfbuzz0b:i386 libharfbuzz0b
```

Are you using or were using some kde ppa's or repos in your sources?

---

