---
title: "apt-get install seems to be broken"
date: 2006-09-29
forum: Desktop Environments
---

### Post by mudra on 2006-09-29
I have been running UBUNTU 6.06 for a few months now with no problems. However, when I have tried to update tonight I get the following error.

> root@UBUNTUM:/var/lib/dpkg# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages will be upgraded:
  amarok amarok-xine ktorrent libssl-dev libssl0.9.8 openssl tor
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.5MB of archives.
After unpacking 102kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
dpkg: can't mmap package info file `/var/lib/dpkg/available': No such device
E: Sub-process /usr/bin/dpkg returned an error code (2)


(We had a thunderstorm earlier which took all the power out, so not sure if that has anything to do with it).

Anyone know how to fix this ? I have tried creating the directory in /var/lib/dpkg but that does not work.

I have tried apt-get -f install, but that didn't help either.

Thanks for any help.

Mudra.

---

### Post by baldy1324 on 2006-09-29
ummm it would help if you copied the dpkg log that returned an error code
```
sudo cat /var/log/dpkg.log
```

---

### Post by powder on 2006-09-29
Give this a shot.

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mudra on 2006-09-30
Please find below the output from car /var/dpkg.log

2006-09-15 08:18:23 status unpacked linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
2006-09-15 08:18:24 status unpacked linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
2006-09-15 08:18:24 upgrade xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-3 7.0.0-8.25.18+2.6.15.11-4
2006-09-15 08:18:24 status half-configured xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-3
2006-09-15 08:18:24 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-3
2006-09-15 08:18:24 status half-installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-3
2006-09-15 08:18:25 status half-installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-3
2006-09-15 08:18:25 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-4
2006-09-15 08:18:26 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-4
2006-09-15 08:18:27 status unpacked automatix 6.5-1-6.06dapper1
2006-09-15 08:18:27 status half-configured automatix 6.5-1-6.06dapper1
2006-09-15 08:18:27 status installed automatix 6.5-1-6.06dapper1
2006-09-15 08:18:27 status unpacked linux-headers-2.6.15-26 2.6.15-26.47
2006-09-15 08:18:27 status half-configured linux-headers-2.6.15-26 2.6.15-26.47
2006-09-15 08:18:27 status installed linux-headers-2.6.15-26 2.6.15-26.47
2006-09-15 08:18:27 status unpacked linux-headers-2.6.15-26-386 2.6.15-26.47
2006-09-15 08:18:27 status half-configured linux-headers-2.6.15-26-386 2.6.15-26.47
2006-09-15 08:18:27 status installed linux-headers-2.6.15-26-386 2.6.15-26.47
2006-09-15 08:18:27 status unpacked linux-image-2.6.15-26-386 2.6.15-26.47
2006-09-15 08:18:27 status half-configured linux-image-2.6.15-26-386 2.6.15-26.47
2006-09-15 08:18:57 status installed linux-image-2.6.15-26-386 2.6.15-26.47
2006-09-15 08:18:57 status unpacked linux-restricted-modules-common 2.6.15.11-4
2006-09-15 08:18:57 status unpacked linux-restricted-modules-common 2.6.15.11-4
2006-09-15 08:18:57 status unpacked linux-restricted-modules-common 2.6.15.11-4
2006-09-15 08:18:57 status unpacked linux-restricted-modules-common 2.6.15.11-4
2006-09-15 08:18:57 status half-configured linux-restricted-modules-common 2.6.15.11-4
2006-09-15 08:18:57 status installed linux-restricted-modules-common 2.6.15.11-4
2006-09-15 08:18:57 status unpacked linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
2006-09-15 08:18:57 status half-configured linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
2006-09-15 08:18:58 status installed linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
2006-09-15 08:18:58 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-4
2006-09-15 08:18:58 status half-configured xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-4
2006-09-15 08:18:58 status installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-4
2006-09-16 09:40:58 upgrade compiz-plugins 0.27-0ubuntu1 0.31-0ubuntu1
2006-09-16 09:40:58 status half-configured compiz-plugins 0.27-0ubuntu1
2006-09-16 09:40:58 status unpacked compiz-plugins 0.27-0ubuntu1
2006-09-16 09:40:58 status half-installed compiz-plugins 0.27-0ubuntu1
2006-09-16 09:40:58 status half-installed compiz-plugins 0.27-0ubuntu1
2006-09-16 09:40:58 status unpacked compiz-plugins 0.31-0ubuntu1
2006-09-16 09:40:58 status unpacked compiz-plugins 0.31-0ubuntu1
2006-09-16 09:40:58 upgrade compiz-gnome 0.0.13.52-0ubuntu1 0.0.13.54-0ubuntu1
2006-09-16 09:40:58 status half-configured compiz-gnome 0.0.13.52-0ubuntu1
2006-09-16 09:40:58 status unpacked compiz-gnome 0.0.13.52-0ubuntu1
2006-09-16 09:40:58 status half-installed compiz-gnome 0.0.13.52-0ubuntu1
2006-09-16 09:40:58 status half-installed compiz-gnome 0.0.13.52-0ubuntu1
2006-09-16 09:40:58 status unpacked compiz-gnome 0.0.13.54-0ubuntu1
2006-09-16 09:40:58 status unpacked compiz-gnome 0.0.13.54-0ubuntu1
2006-09-16 09:40:58 upgrade compiz-core 0.0.13.52-0ubuntu1 0.0.13.54-0ubuntu1
2006-09-16 09:40:58 status half-configured compiz-core 0.0.13.52-0ubuntu1
2006-09-16 09:40:58 status unpacked compiz-core 0.0.13.52-0ubuntu1
2006-09-16 09:40:58 status half-installed compiz-core 0.0.13.52-0ubuntu1
2006-09-16 09:40:59 status half-installed compiz-core 0.0.13.52-0ubuntu1
2006-09-16 09:40:59 status unpacked compiz-core 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status unpacked compiz-core 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 upgrade compiz 0.0.13.52-0ubuntu1 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status half-configured compiz 0.0.13.52-0ubuntu1
2006-09-16 09:40:59 status unpacked compiz 0.0.13.52-0ubuntu1
2006-09-16 09:40:59 status half-installed compiz 0.0.13.52-0ubuntu1
2006-09-16 09:40:59 status half-installed compiz 0.0.13.52-0ubuntu1
2006-09-16 09:40:59 status unpacked compiz 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status unpacked compiz 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status unpacked compiz-core 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status half-configured compiz-core 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status installed compiz-core 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status unpacked compiz-plugins 0.31-0ubuntu1
2006-09-16 09:40:59 status half-configured compiz-plugins 0.31-0ubuntu1
2006-09-16 09:40:59 status installed compiz-plugins 0.31-0ubuntu1
2006-09-16 09:40:59 status unpacked compiz-gnome 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status half-configured compiz-gnome 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status installed compiz-gnome 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status unpacked compiz 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status half-configured compiz 0.0.13.54-0ubuntu1
2006-09-16 09:40:59 status installed compiz 0.0.13.54-0ubuntu1
2006-09-18 21:30:01 upgrade automatix 6.5-1-6.06dapper1 6.5-3-6.06dapper1
2006-09-18 21:30:01 status half-configured automatix 6.5-1-6.06dapper1
2006-09-18 21:30:01 status unpacked automatix 6.5-1-6.06dapper1
2006-09-18 21:30:01 status half-installed automatix 6.5-1-6.06dapper1
2006-09-18 21:30:01 status half-installed automatix 6.5-1-6.06dapper1
2006-09-18 21:30:01 status unpacked automatix 6.5-3-6.06dapper1
2006-09-18 21:30:01 status unpacked automatix 6.5-3-6.06dapper1
2006-09-18 21:30:02 upgrade compiz-plugins 0.31-0ubuntu1 0.37-0ubuntu1
2006-09-18 21:30:02 status half-configured compiz-plugins 0.31-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz-plugins 0.31-0ubuntu1
2006-09-18 21:30:02 status half-installed compiz-plugins 0.31-0ubuntu1
2006-09-18 21:30:02 status half-installed compiz-plugins 0.31-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz-plugins 0.37-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz-plugins 0.37-0ubuntu1
2006-09-18 21:30:02 upgrade compiz-gnome 0.0.13.54-0ubuntu1 0.0.13.57-0ubuntu1
2006-09-18 21:30:02 status half-configured compiz-gnome 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz-gnome 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status half-installed compiz-gnome 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status half-installed compiz-gnome 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz-gnome 0.0.13.57-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz-gnome 0.0.13.57-0ubuntu1
2006-09-18 21:30:02 upgrade compiz-core 0.0.13.54-0ubuntu1 0.0.13.57-0ubuntu1
2006-09-18 21:30:02 status half-configured compiz-core 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz-core 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status half-installed compiz-core 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status half-installed compiz-core 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz-core 0.0.13.57-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz-core 0.0.13.57-0ubuntu1
2006-09-18 21:30:02 upgrade compiz 0.0.13.54-0ubuntu1 0.0.13.57-0ubuntu1
2006-09-18 21:30:02 status half-configured compiz 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status half-installed compiz 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status half-installed compiz 0.0.13.54-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz 0.0.13.57-0ubuntu1
2006-09-18 21:30:02 status unpacked compiz 0.0.13.57-0ubuntu1
2006-09-18 21:30:03 status unpacked automatix 6.5-3-6.06dapper1
2006-09-18 21:30:03 status half-configured automatix 6.5-3-6.06dapper1
2006-09-18 21:30:03 status installed automatix 6.5-3-6.06dapper1
2006-09-18 21:30:03 status unpacked compiz-core 0.0.13.57-0ubuntu1
2006-09-18 21:30:03 status half-configured compiz-core 0.0.13.57-0ubuntu1
2006-09-18 21:30:03 status installed compiz-core 0.0.13.57-0ubuntu1
2006-09-18 21:30:03 status unpacked compiz-plugins 0.37-0ubuntu1
2006-09-18 21:30:03 status half-configured compiz-plugins 0.37-0ubuntu1
2006-09-18 21:30:03 status installed compiz-plugins 0.37-0ubuntu1
2006-09-18 21:30:03 status unpacked compiz-gnome 0.0.13.57-0ubuntu1
2006-09-18 21:30:03 status half-configured compiz-gnome 0.0.13.57-0ubuntu1
2006-09-18 21:30:03 status installed compiz-gnome 0.0.13.57-0ubuntu1
2006-09-18 21:30:03 status unpacked compiz 0.0.13.57-0ubuntu1
2006-09-18 21:30:03 status half-configured compiz 0.0.13.57-0ubuntu1
2006-09-18 21:30:03 status installed compiz 0.0.13.57-0ubuntu1
2006-09-19 18:52:37 upgrade libgnutls12 1.2.9-2ubuntu1 1.2.9-2ubuntu1.1
2006-09-19 18:52:37 status half-configured libgnutls12 1.2.9-2ubuntu1
2006-09-19 18:52:37 status unpacked libgnutls12 1.2.9-2ubuntu1
2006-09-19 18:52:37 status half-installed libgnutls12 1.2.9-2ubuntu1
2006-09-19 18:52:37 status half-installed libgnutls12 1.2.9-2ubuntu1
2006-09-19 18:52:37 status unpacked libgnutls12 1.2.9-2ubuntu1.1
2006-09-19 18:52:37 status unpacked libgnutls12 1.2.9-2ubuntu1.1
2006-09-19 18:52:37 upgrade libclamav1 0.88.2-1ubuntu1 0.88.2-1ubuntu1.1
2006-09-19 18:52:37 status half-configured libclamav1 0.88.2-1ubuntu1
2006-09-19 18:52:37 status unpacked libclamav1 0.88.2-1ubuntu1
2006-09-19 18:52:37 status half-installed libclamav1 0.88.2-1ubuntu1
2006-09-19 18:52:38 status half-installed libclamav1 0.88.2-1ubuntu1
2006-09-19 18:52:38 status unpacked libclamav1 0.88.2-1ubuntu1.1
2006-09-19 18:52:38 status unpacked libclamav1 0.88.2-1ubuntu1.1
2006-09-19 18:52:38 upgrade clamav-freshclam 0.88.2-1ubuntu1 0.88.2-1ubuntu1.1
2006-09-19 18:52:38 status half-configured clamav-freshclam 0.88.2-1ubuntu1
2006-09-19 18:52:39 status unpacked clamav-freshclam 0.88.2-1ubuntu1
2006-09-19 18:52:39 status half-installed clamav-freshclam 0.88.2-1ubuntu1
2006-09-19 18:52:39 status half-installed clamav-freshclam 0.88.2-1ubuntu1
2006-09-19 18:52:39 status unpacked clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:52:39 status unpacked clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:52:39 upgrade clamav-base 0.88.2-1ubuntu1 0.88.2-1ubuntu1.1
2006-09-19 18:52:39 status half-configured clamav-base 0.88.2-1ubuntu1
2006-09-19 18:52:39 status unpacked clamav-base 0.88.2-1ubuntu1
2006-09-19 18:52:39 status half-installed clamav-base 0.88.2-1ubuntu1
2006-09-19 18:52:40 status half-installed clamav-base 0.88.2-1ubuntu1
2006-09-19 18:52:40 status unpacked clamav-base 0.88.2-1ubuntu1.1
2006-09-19 18:52:40 status unpacked clamav-base 0.88.2-1ubuntu1.1
2006-09-19 18:52:40 upgrade clamav 0.88.2-1ubuntu1 0.88.2-1ubuntu1.1
2006-09-19 18:52:40 status half-configured clamav 0.88.2-1ubuntu1
2006-09-19 18:52:40 status unpacked clamav 0.88.2-1ubuntu1
2006-09-19 18:52:40 status half-installed clamav 0.88.2-1ubuntu1
2006-09-19 18:52:40 status half-installed clamav 0.88.2-1ubuntu1
2006-09-19 18:52:40 status unpacked clamav 0.88.2-1ubuntu1.1
2006-09-19 18:52:40 status unpacked clamav 0.88.2-1ubuntu1.1
2006-09-19 18:52:40 upgrade libgnutls11 1.0.16-14ubuntu1 1.0.16-14ubuntu1.1
2006-09-19 18:52:40 status half-configured libgnutls11 1.0.16-14ubuntu1
2006-09-19 18:52:40 status unpacked libgnutls11 1.0.16-14ubuntu1
2006-09-19 18:52:40 status half-installed libgnutls11 1.0.16-14ubuntu1
2006-09-19 18:52:40 status half-installed libgnutls11 1.0.16-14ubuntu1
2006-09-19 18:52:40 status unpacked libgnutls11 1.0.16-14ubuntu1.1
2006-09-19 18:52:40 status unpacked libgnutls11 1.0.16-14ubuntu1.1
2006-09-19 18:52:40 install linux-image-2.6.15-27-386 <none> 2.6.15-27.48
2006-09-19 18:52:40 status half-installed linux-image-2.6.15-27-386 2.6.15-27.48
2006-09-19 18:52:42 status unpacked linux-image-2.6.15-27-386 2.6.15-27.48
2006-09-19 18:52:42 status unpacked linux-image-2.6.15-27-386 2.6.15-27.48
2006-09-19 18:52:42 upgrade linux-image-386 2.6.15.24 2.6.15.25
2006-09-19 18:52:42 status half-configured linux-image-386 2.6.15.24
2006-09-19 18:52:42 status unpacked linux-image-386 2.6.15.24
2006-09-19 18:52:42 status half-installed linux-image-386 2.6.15.24
2006-09-19 18:52:42 status half-installed linux-image-386 2.6.15.24
2006-09-19 18:52:42 status unpacked linux-image-386 2.6.15.25
2006-09-19 18:52:42 status unpacked linux-image-386 2.6.15.25
2006-09-19 18:52:42 upgrade linux-restricted-modules-common 2.6.15.11-4 2.6.15.11-5
2006-09-19 18:52:42 status half-configured linux-restricted-modules-common 2.6.15.11-4
2006-09-19 18:52:42 status unpacked linux-restricted-modules-common 2.6.15.11-4
2006-09-19 18:52:42 status half-installed linux-restricted-modules-common 2.6.15.11-4
2006-09-19 18:52:42 status half-installed linux-restricted-modules-common 2.6.15.11-4
2006-09-19 18:52:42 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 18:52:42 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 18:52:42 upgrade xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-4 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 18:52:42 status half-configured xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-4
2006-09-19 18:52:42 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-4
2006-09-19 18:52:42 status half-installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-4
2006-09-19 18:52:43 status half-installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-4
2006-09-19 18:52:43 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 18:52:43 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 18:52:44 status unpacked libgnutls12 1.2.9-2ubuntu1.1
2006-09-19 18:52:44 status half-configured libgnutls12 1.2.9-2ubuntu1.1
2006-09-19 18:52:54 status installed libgnutls12 1.2.9-2ubuntu1.1
2006-09-19 18:52:54 status unpacked libclamav1 0.88.2-1ubuntu1.1
2006-09-19 18:52:54 status half-configured libclamav1 0.88.2-1ubuntu1.1
2006-09-19 18:52:54 status installed libclamav1 0.88.2-1ubuntu1.1
2006-09-19 18:52:54 status unpacked clamav-base 0.88.2-1ubuntu1.1
2006-09-19 18:52:54 status unpacked clamav-base 0.88.2-1ubuntu1.1
2006-09-19 18:52:54 status half-configured clamav-base 0.88.2-1ubuntu1.1
2006-09-19 18:52:59 status installed clamav-base 0.88.2-1ubuntu1.1
2006-09-19 18:52:59 status unpacked clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:52:59 status unpacked clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:52:59 status unpacked clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:52:59 status unpacked clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:52:59 status unpacked clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:52:59 status unpacked clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:52:59 status unpacked clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:52:59 status unpacked clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:52:59 status half-configured clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:53:04 status installed clamav-freshclam 0.88.2-1ubuntu1.1
2006-09-19 18:53:04 status unpacked clamav 0.88.2-1ubuntu1.1
2006-09-19 18:53:04 status half-configured clamav 0.88.2-1ubuntu1.1
2006-09-19 18:53:04 status installed clamav 0.88.2-1ubuntu1.1
2006-09-19 18:53:04 status unpacked libgnutls11 1.0.16-14ubuntu1.1
2006-09-19 18:53:04 status half-configured libgnutls11 1.0.16-14ubuntu1.1
2006-09-19 18:53:05 status installed libgnutls11 1.0.16-14ubuntu1.1
2006-09-19 18:53:05 status unpacked linux-image-2.6.15-27-386 2.6.15-27.48
2006-09-19 18:53:05 status half-configured linux-image-2.6.15-27-386 2.6.15-27.48
2006-09-19 18:53:47 status installed linux-image-2.6.15-27-386 2.6.15-27.48
2006-09-19 18:53:47 status unpacked linux-image-386 2.6.15.25
2006-09-19 18:53:47 status half-configured linux-image-386 2.6.15.25
2006-09-19 18:53:47 status installed linux-image-386 2.6.15.25
2006-09-19 18:53:47 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 18:53:47 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 18:53:47 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 18:53:47 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 18:53:47 status half-configured linux-restricted-modules-common 2.6.15.11-5
2006-09-19 18:53:47 status installed linux-restricted-modules-common 2.6.15.11-5
2006-09-19 18:53:47 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 18:53:47 status half-configured xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 18:53:47 status installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:20:47 status installed linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
2006-09-19 19:21:06 remove linux-restricted-modules-2.6.15-26-386 2.6.15.11-4 2.6.15.11-4
2006-09-19 19:21:06 status half-configured linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
2006-09-19 19:21:06 status half-installed linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
2006-09-19 19:21:25 status config-files linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
2006-09-19 19:21:25 status config-files linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
2006-09-19 19:21:25 status installed linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:21:25 remove linux-restricted-modules-common 2.6.15.11-5 2.6.15.11-5
2006-09-19 19:21:25 status half-configured linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:21:25 status half-installed linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:21:25 status config-files linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:21:25 status config-files linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:22:24 install linux-restricted-modules-common 2.6.15.11-5 2.6.15.11-5
2006-09-19 19:22:24 status half-installed linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:22:24 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:22:24 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:22:24 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:22:24 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:22:24 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:22:24 status unpacked linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:22:24 status half-configured linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:22:24 status installed linux-restricted-modules-common 2.6.15.11-5
2006-09-19 19:22:58 status installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:22:58 remove xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:22:58 status half-configured xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:22:58 status half-installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:23:07 status config-files xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:23:07 status config-files xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:23:17 install xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:23:17 status half-installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:23:19 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:23:19 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:23:19 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:23:19 status half-configured xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 19:23:19 status installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:02:16 install linux-restricted-modules-2.6.15-27-386 <none> 2.6.15.11-5
2006-09-19 20:02:16 status half-installed linux-restricted-modules-2.6.15-27-386 2.6.15.11-5
2006-09-19 20:02:17 status unpacked linux-restricted-modules-2.6.15-27-386 2.6.15.11-5
2006-09-19 20:02:17 status unpacked linux-restricted-modules-2.6.15-27-386 2.6.15.11-5
2006-09-19 20:02:17 status unpacked linux-restricted-modules-2.6.15-27-386 2.6.15.11-5
2006-09-19 20:02:17 status half-configured linux-restricted-modules-2.6.15-27-386 2.6.15.11-5
2006-09-19 20:02:22 status installed linux-restricted-modules-2.6.15-27-386 2.6.15.11-5
2006-09-19 20:02:55 status installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:02:56 remove xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:02:56 status half-configured xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:02:56 status half-installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:02:56 status config-files xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:02:56 status config-files xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:03:01 install xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:03:01 status half-installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:03:01 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:03:01 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:03:02 status unpacked xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:03:02 status half-configured xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:03:02 status installed xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5
2006-09-19 20:04:17 upgrade gzip 1.3.5-12 1.3.5-12ubuntu0.1
2006-09-19 20:04:17 status half-configured gzip 1.3.5-12
2006-09-19 20:04:17 status unpacked gzip 1.3.5-12
2006-09-19 20:04:17 status half-installed gzip 1.3.5-12
2006-09-19 20:04:17 status half-installed gzip 1.3.5-12
2006-09-19 20:04:17 status unpacked gzip 1.3.5-12ubuntu0.1
2006-09-19 20:04:17 status unpacked gzip 1.3.5-12ubuntu0.1
2006-09-19 20:04:18 status unpacked gzip 1.3.5-12ubuntu0.1
2006-09-19 20:04:18 status half-configured gzip 1.3.5-12ubuntu0.1
2006-09-19 20:04:18 status installed gzip 1.3.5-12ubuntu0.1
2006-09-20 18:56:53 upgrade flashplugin-nonfree 7.0.63.3ubuntu3 7.0.68~ubuntu1~dapper1
2006-09-20 18:56:53 status half-configured flashplugin-nonfree 7.0.63.3ubuntu3
2006-09-20 18:56:53 status unpacked flashplugin-nonfree 7.0.63.3ubuntu3
2006-09-20 18:56:53 status half-installed flashplugin-nonfree 7.0.63.3ubuntu3
2006-09-20 18:56:53 status half-installed flashplugin-nonfree 7.0.63.3ubuntu3
2006-09-20 18:56:53 status unpacked flashplugin-nonfree 7.0.68~ubuntu1~dapper1
2006-09-20 18:56:53 status unpacked flashplugin-nonfree 7.0.68~ubuntu1~dapper1
2006-09-20 18:56:53 upgrade libk3b2 0.12.14-0ubuntu7 0.12.17-1ubuntu3~dapper1
2006-09-20 18:56:53 status half-configured libk3b2 0.12.14-0ubuntu7
2006-09-20 18:56:53 status unpacked libk3b2 0.12.14-0ubuntu7
2006-09-20 18:56:53 status half-installed libk3b2 0.12.14-0ubuntu7
2006-09-20 18:56:53 status half-installed libk3b2 0.12.14-0ubuntu7
2006-09-20 18:56:53 status unpacked libk3b2 0.12.17-1ubuntu3~dapper1
2006-09-20 18:56:53 status unpacked libk3b2 0.12.17-1ubuntu3~dapper1
2006-09-20 18:56:53 upgrade k3b 0.12.14-0ubuntu7 0.12.17-1ubuntu3~dapper1
2006-09-20 18:56:53 status half-configured k3b 0.12.14-0ubuntu7
2006-09-20 18:56:53 status unpacked k3b 0.12.14-0ubuntu7
2006-09-20 18:56:53 status half-installed k3b 0.12.14-0ubuntu7
2006-09-20 18:56:54 status half-installed k3b 0.12.14-0ubuntu7
2006-09-20 18:56:54 status unpacked k3b 0.12.17-1ubuntu3~dapper1
2006-09-20 18:56:54 status unpacked k3b 0.12.17-1ubuntu3~dapper1
2006-09-20 18:56:55 status unpacked flashplugin-nonfree 7.0.68~ubuntu1~dapper1
2006-09-20 18:56:55 status unpacked flashplugin-nonfree 7.0.68~ubuntu1~dapper1
2006-09-20 18:56:55 status half-configured flashplugin-nonfree 7.0.68~ubuntu1~dapper1
2006-09-20 18:57:10 status unpacked libk3b2 0.12.17-1ubuntu3~dapper1
2006-09-20 18:57:10 status half-configured libk3b2 0.12.17-1ubuntu3~dapper1
2006-09-20 18:57:10 status installed libk3b2 0.12.17-1ubuntu3~dapper1
2006-09-20 18:57:10 status unpacked k3b 0.12.17-1ubuntu3~dapper1
2006-09-20 18:57:10 status half-configured k3b 0.12.17-1ubuntu3~dapper1
2006-09-20 18:57:13 status installed k3b 0.12.17-1ubuntu3~dapper1
2006-09-20 18:57:14 status half-configured flashplugin-nonfree 7.0.68~ubuntu1~dapper1
2006-09-22 20:08:40 upgrade opera 9.0-20060616.6 9.02-20060919.6
2006-09-22 20:08:40 status half-configured opera 9.0-20060616.6
2006-09-22 20:08:40 status unpacked opera 9.0-20060616.6
2006-09-22 20:08:40 status half-installed opera 9.0-20060616.6
2006-09-22 20:08:41 status half-installed opera 9.0-20060616.6
2006-09-22 20:08:41 status unpacked opera 9.02-20060919.6
2006-09-22 20:08:42 status unpacked opera 9.02-20060919.6
2006-09-22 20:08:42 status unpacked opera 9.02-20060919.6
2006-09-22 20:08:42 status unpacked opera 9.02-20060919.6
2006-09-22 20:08:42 status unpacked opera 9.02-20060919.6
2006-09-22 20:08:42 status half-configured opera 9.02-20060919.6
2006-09-22 20:08:44 status installed opera 9.02-20060919.6
2006-09-23 09:33:43 upgrade flashplugin-nonfree 7.0.68~ubuntu1~dapper1 7.0.68~ubuntu2~dapper1
2006-09-23 09:33:43 status half-configured flashplugin-nonfree 7.0.68~ubuntu1~dapper1
2006-09-23 09:33:44 status unpacked flashplugin-nonfree 7.0.68~ubuntu1~dapper1
2006-09-23 09:33:44 status half-installed flashplugin-nonfree 7.0.68~ubuntu1~dapper1
2006-09-23 09:33:44 status half-installed flashplugin-nonfree 7.0.68~ubuntu1~dapper1
2006-09-23 09:33:44 status unpacked flashplugin-nonfree 7.0.68~ubuntu2~dapper1
2006-09-23 09:33:44 status unpacked flashplugin-nonfree 7.0.68~ubuntu2~dapper1
2006-09-23 09:33:44 upgrade amarok-xine 2:1.4.2-0ubuntu2~dapper1 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:33:44 status half-configured amarok-xine 2:1.4.2-0ubuntu2~dapper1
2006-09-23 09:33:44 status unpacked amarok-xine 2:1.4.2-0ubuntu2~dapper1
2006-09-23 09:33:44 status half-installed amarok-xine 2:1.4.2-0ubuntu2~dapper1
2006-09-23 09:33:44 status half-installed amarok-xine 2:1.4.2-0ubuntu2~dapper1
2006-09-23 09:33:44 status unpacked amarok-xine 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:33:44 status unpacked amarok-xine 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:33:45 upgrade amarok 2:1.4.2-0ubuntu2~dapper1 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:33:45 status half-configured amarok 2:1.4.2-0ubuntu2~dapper1
2006-09-23 09:33:45 status unpacked amarok 2:1.4.2-0ubuntu2~dapper1
2006-09-23 09:33:45 status half-installed amarok 2:1.4.2-0ubuntu2~dapper1
2006-09-23 09:33:46 status half-installed amarok 2:1.4.2-0ubuntu2~dapper1
2006-09-23 09:33:47 status unpacked amarok 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:33:47 status unpacked amarok 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:33:48 upgrade automatix 6.5-3-6.06dapper1 6.5-4-6.06dapper1
2006-09-23 09:33:48 status half-configured automatix 6.5-3-6.06dapper1
2006-09-23 09:33:48 status unpacked automatix 6.5-3-6.06dapper1
2006-09-23 09:33:48 status half-installed automatix 6.5-3-6.06dapper1
2006-09-23 09:33:48 status half-installed automatix 6.5-3-6.06dapper1
2006-09-23 09:33:48 status unpacked automatix 6.5-4-6.06dapper1
2006-09-23 09:33:48 status unpacked automatix 6.5-4-6.06dapper1
2006-09-23 09:33:49 upgrade firefox-gnome-support 1.5.dfsg+1.5.0.5-0ubuntu6.06.1 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:49 status half-configured firefox-gnome-support 1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:49 status unpacked firefox-gnome-support 1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:49 status half-installed firefox-gnome-support 1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:49 status half-installed firefox-gnome-support 1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:49 status unpacked firefox-gnome-support 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:49 status unpacked firefox-gnome-support 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:49 upgrade libnspr4 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:49 status half-configured libnspr4 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:49 status unpacked libnspr4 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:49 status half-installed libnspr4 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:49 status half-installed libnspr4 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:49 status unpacked libnspr4 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:49 status unpacked libnspr4 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:50 upgrade libnss3 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:50 status half-configured libnss3 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:50 status unpacked libnss3 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:50 status half-installed libnss3 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:50 status half-installed libnss3 2:1.firefox1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:50 status unpacked libnss3 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:50 status unpacked libnss3 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:50 upgrade firefox 1.5.dfsg+1.5.0.5-0ubuntu6.06.1 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:50 status half-configured firefox 1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:50 status unpacked firefox 1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:50 status half-installed firefox 1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:53 status half-installed firefox 1.5.dfsg+1.5.0.5-0ubuntu6.06.1
2006-09-23 09:33:54 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:54 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:33:54 install libio-zlib-perl <none> 1.04-1
2006-09-23 09:33:54 status half-installed libio-zlib-perl 1.04-1
2006-09-23 09:33:56 status unpacked libio-zlib-perl 1.04-1
2006-09-23 09:33:56 status unpacked libio-zlib-perl 1.04-1
2006-09-23 09:33:57 install libarchive-tar-perl <none> 1.26-2
2006-09-23 09:33:57 status half-installed libarchive-tar-perl 1.26-2
2006-09-23 09:33:57 status unpacked libarchive-tar-perl 1.26-2
2006-09-23 09:33:57 status unpacked libarchive-tar-perl 1.26-2
2006-09-23 09:33:57 install libwww-perl <none> 5.803-4
2006-09-23 09:33:57 status half-installed libwww-perl 5.803-4
2006-09-23 09:33:57 status unpacked libwww-perl 5.803-4
2006-09-23 09:33:57 status unpacked libwww-perl 5.803-4
2006-09-23 09:33:58 install libhtml-tree-perl <none> 3.19.01-1
2006-09-23 09:33:58 status half-installed libhtml-tree-perl 3.19.01-1
2006-09-23 09:33:58 status unpacked libhtml-tree-perl 3.19.01-1
2006-09-23 09:33:58 status unpacked libhtml-tree-perl 3.19.01-1
2006-09-23 09:33:58 upgrade mozilla-mplayer 3.17-1ubuntu1 3.25-7ubuntu1~dapper1
2006-09-23 09:33:58 status half-configured mozilla-mplayer 3.17-1ubuntu1
2006-09-23 09:33:58 status unpacked mozilla-mplayer 3.17-1ubuntu1
2006-09-23 09:33:58 status half-installed mozilla-mplayer 3.17-1ubuntu1
2006-09-23 09:33:58 status half-installed mozilla-mplayer 3.17-1ubuntu1
2006-09-23 09:33:58 status unpacked mozilla-mplayer 3.25-7ubuntu1~dapper1
2006-09-23 09:33:58 status unpacked mozilla-mplayer 3.25-7ubuntu1~dapper1
2006-09-23 09:33:59 upgrade spamassassin 3.1.0a-2ubuntu1.1 3.1.3-1ubuntu1~dapper1
2006-09-23 09:33:59 status half-configured spamassassin 3.1.0a-2ubuntu1.1
2006-09-23 09:34:00 status unpacked spamassassin 3.1.0a-2ubuntu1.1
2006-09-23 09:34:00 status half-installed spamassassin 3.1.0a-2ubuntu1.1
2006-09-23 09:34:00 status half-installed spamassassin 3.1.0a-2ubuntu1.1
2006-09-23 09:34:00 status unpacked spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:00 status unpacked spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:00 status unpacked flashplugin-nonfree 7.0.68~ubuntu2~dapper1
2006-09-23 09:34:00 status unpacked flashplugin-nonfree 7.0.68~ubuntu2~dapper1
2006-09-23 09:34:00 status half-configured flashplugin-nonfree 7.0.68~ubuntu2~dapper1
2006-09-23 09:34:32 status installed flashplugin-nonfree 7.0.68~ubuntu2~dapper1
2006-09-23 09:34:32 status unpacked automatix 6.5-4-6.06dapper1
2006-09-23 09:34:32 status half-configured automatix 6.5-4-6.06dapper1
2006-09-23 09:34:32 status installed automatix 6.5-4-6.06dapper1
2006-09-23 09:34:32 status unpacked libnspr4 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:32 status half-configured libnspr4 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:32 status installed libnspr4 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:32 status unpacked libnss3 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:32 status half-configured libnss3 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:32 status installed libnss3 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:32 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:32 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:33 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:33 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:33 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:33 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:33 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:33 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:33 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:33 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:33 status unpacked firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:33 status half-configured firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:34 status installed firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:34 status unpacked firefox-gnome-support 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:34 status half-configured firefox-gnome-support 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:34 status installed firefox-gnome-support 1.5.dfsg+1.5.0.7-ubuntu0.6.06
2006-09-23 09:34:34 status unpacked libio-zlib-perl 1.04-1
2006-09-23 09:34:34 status half-configured libio-zlib-perl 1.04-1
2006-09-23 09:34:34 status installed libio-zlib-perl 1.04-1
2006-09-23 09:34:34 status unpacked libarchive-tar-perl 1.26-2
2006-09-23 09:34:34 status half-configured libarchive-tar-perl 1.26-2
2006-09-23 09:34:34 status installed libarchive-tar-perl 1.26-2
2006-09-23 09:34:34 status unpacked mozilla-mplayer 3.25-7ubuntu1~dapper1
2006-09-23 09:34:34 status unpacked mozilla-mplayer 3.25-7ubuntu1~dapper1
2006-09-23 09:34:34 status unpacked mozilla-mplayer 3.25-7ubuntu1~dapper1
2006-09-23 09:34:34 status half-configured mozilla-mplayer 3.25-7ubuntu1~dapper1
2006-09-23 09:34:34 status installed mozilla-mplayer 3.25-7ubuntu1~dapper1
2006-09-23 09:34:34 status unpacked amarok-xine 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:34:34 status half-configured amarok-xine 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:34:34 status installed amarok-xine 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:34:34 status unpacked libwww-perl 5.803-4
2006-09-23 09:34:34 status half-configured libwww-perl 5.803-4
2006-09-23 09:34:34 status installed libwww-perl 5.803-4
2006-09-23 09:34:34 status unpacked spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:34 status unpacked spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:34 status unpacked spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:34 status unpacked spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:34 status unpacked spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:34 status unpacked spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:34 status unpacked spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:34 status unpacked spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:34 status unpacked spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:34 status half-configured spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:35 status installed spamassassin 3.1.3-1ubuntu1~dapper1
2006-09-23 09:34:35 status unpacked amarok 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:34:35 status unpacked amarok 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:34:35 status half-configured amarok 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:34:38 status installed amarok 2:1.4.3-0ubuntu6~dapper1
2006-09-23 09:34:38 status unpacked libhtml-tree-perl 3.19.01-1
2006-09-23 09:34:38 status half-configured libhtml-tree-perl 3.19.01-1
2006-09-23 09:34:38 status installed libhtml-tree-perl 3.19.01-1
2006-09-25 17:47:26 upgrade automatix 6.5-4-6.06dapper1 6.5-5-6.06dapper1
2006-09-25 17:47:26 status half-configured automatix 6.5-4-6.06dapper1
2006-09-25 17:47:26 status unpacked automatix 6.5-4-6.06dapper1
2006-09-25 17:47:26 status half-installed automatix 6.5-4-6.06dapper1
2006-09-25 17:47:29 status half-installed automatix 6.5-4-6.06dapper1
2006-09-25 17:47:30 status unpacked automatix 6.5-5-6.06dapper1
2006-09-25 17:47:30 status unpacked automatix 6.5-5-6.06dapper1
2006-09-25 17:47:32 status unpacked automatix 6.5-5-6.06dapper1
2006-09-25 17:47:32 status half-configured automatix 6.5-5-6.06dapper1
2006-09-25 17:47:32 status installed automatix 6.5-5-6.06dapper1


I am not sure what any of that means.

I also tried 

apt-get clean
apt-get update
apt-get upgrade

and I got the same error.

Hope there is something else I can try.

Thanks for all the help.

Murda

---

