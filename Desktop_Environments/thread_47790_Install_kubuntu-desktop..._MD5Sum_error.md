---
title: "Install kubuntu-desktop... MD5Sum error?"
date: 2005-07-10
forum: Desktop Environments
---

### Post by ryanazar on 2005-07-10
Hello, first of all I want to congradulate everyone involved with the Ubuntu/Kubuntu project :). Installing an Ubuntu partition on my G4 ibook worked flawlessly, as well as on my amd Pc.

I installed the lastest release of Ubuntu PPC, and everything is working great. I would rather use KDE than Gnome, and also I like to have more than one WM available depending on how I want my system to look.

I tried using the command 'sudo apt-get install kubuntu-desktop', and this is the log:

```

ryan@ubuntu:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  k3b k3blibs kdebase kdegraphics kdemultimedia kdemultimedia-kappfinder-data
  kdepim kdeutils kdm kfind kfloppy kgamma kmailcvt kmilo kmix konq-plugins
  konqueror ktnef kubuntu-default-settings kwalletmanager libarts1-xine
  libmad0
Suggested packages:
  k3b-i18n normalize toolame sox movixmaker-2 cdrdao kdepim-doc-html
  kdeaddons-doc-html konq-speaker
Recommended packages:
  vcdimager xfonts-konsole
The following NEW packages will be installed:
  k3b k3blibs kdebase kdegraphics kdemultimedia kdemultimedia-kappfinder-data
  kdepim kdeutils kdm kfind kfloppy kgamma kmailcvt kmilo kmix konq-plugins
  konqueror ktnef kubuntu-default-settings kubuntu-desktop kwalletmanager
  libarts1-xine libmad0
0 upgraded, 23 newly installed, 0 to remove and 0 not upgraded.
Need to get 1389kB/8731kB of archives.
After unpacking 24.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com hoary/main libmad0 0.15.1b-1 [79.5kB]
Get:2 http://us.archive.ubuntu.com hoary/main kfind 4:3.4.0-0ubuntu18 [171kB]
Get:3 http://us.archive.ubuntu.com hoary/main kgamma 4:3.4.0-0ubuntu3 [73.7kB]
Get:4 http://us.archive.ubuntu.com hoary/main kdemultimedia-kappfinder-data 4:3.4.0-0ubuntu3 [19.5kB]
Get:5 http://us.archive.ubuntu.com hoary/main kmix 4:3.4.0-0ubuntu3 [350kB]
Get:6 http://us.archive.ubuntu.com hoary/main libarts1-xine 4:3.4.0-0ubuntu3 [94.3kB]
Get:7 http://us.archive.ubuntu.com hoary/main kmailcvt 4:3.4.0-0ubuntu10 [96.7kB]
Get:8 http://us.archive.ubuntu.com hoary/main ktnef 4:3.4.0-0ubuntu10 [80.5kB]
Get:9 http://us.archive.ubuntu.com hoary/main kfloppy 4:3.4.0-0ubuntu2 [70.1kB]
Get:10 http://us.archive.ubuntu.com hoary/main kmilo 4:3.4.0-0ubuntu2 [163kB]
Get:11 http://us.archive.ubuntu.com hoary/main kwalletmanager 4:3.4.0-0ubuntu2 [181kB]
Get:12 http://us.archive.ubuntu.com hoary/main kdeutils 4:3.4.0-0ubuntu2 [9564B]Fetched 1389kB in 8s (155kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-1_powerpc.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdebase/kfind_3.4.0-0ubuntu18_powerpc.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kgamma_3.4.0-0ubuntu3_powerpc.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kdemultimedia-kappfinder-data_3.4.0-0ubuntu3_powerpc.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kmix_3.4.0-0ubuntu3_powerpc.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/libarts1-xine_3.4.0-0ubuntu3_powerpc.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/kmailcvt_3.4.0-0ubuntu10_powerpc.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdepim/ktnef_3.4.0-0ubuntu10_powerpc.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kfloppy_3.4.0-0ubuntu2_powerpc.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kmilo_3.4.0-0ubuntu2_powerpc.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kwalletmanager_3.4.0-0ubuntu2_powerpc.deb  MD5Sum mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeutils/kdeutils_3.4.0-0ubuntu2_all.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ryan@ubuntu:~$

```

After 'Get:12' there seems to be MD5Sum mismatch errors. Does anyone know why that is? Here is my /etc/apt/sources.list file (with the commented lines taken out to save space).
```

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Please note I followed the suggestions the terminal gave me: using apt-get update and using --fix-missing

Thanks for all your help  :-)

---

### Post by ltmon on 2005-07-10
The us.archive.ubuntu.org seems to be having problems of late.

Try using simply archive.ubuntu.org for a while until the servers are behaving properly again.

L.

---

### Post by ryanazar on 2005-07-10
Thankyou. Everything works perfectly now, glad it has nothing to do with my system  \\:D/ .

Thanks again!

Ryan

---

