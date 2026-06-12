---
title: "DVD Burner not visible in Disks but is present in lshw"
date: 2016-02-24
forum: Desktop Environments
---

### Post by Paul_Alexander on 2016-02-24
Ubuntu 14.04. Fresh install on a 2009 stock desktop PC with 6GB RAM and a modern big HDD. I am trying to play a DVD movie (original manufacturer DVD) on it.
I have installed the following, but it seems the css library is invalid, but I assume this is ok.

```
sudo apt-get install libdvdcss libdvdread4 libdvdnav4

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'libdvdcss' has no installation candidate
```

I then installed VLC Media Player from the software center and it installed without error.

I  put the DVD in, started VLC PLayer, pointed it to the correct drive, and hit play, but it will not play. Nothing, no sound or  video. The drive spins up though. It also ejects.

I tried both the DVD Reader and the DVD Burner optical drives - neither works. Both are present and working though. For instance, they are both visible in the Disks GUI util and via lshw -class disk. I can also burn files to a DVD.

---

### Post by QDR06VV9 on 2016-02-26
Here is the Problem
```
Package libdvdcss is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source E: Package 'libdvdcss' has no installation candidate
```
If you have installed *ubuntu-restricted-extras this has already been installed automatically for you)
 ```
sudo apt-get install libdvdread4
```
  Then open a terminal window and execute:
  ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
If you still see that same Error from above then do this in the terminal
```
curl ftp://ftp.videolan.org/pub/debian/videolan-apt.asc | sudo apt-key add -  echo "deb ftp://ftp.videolan.org/pub/debian/stable ./" | sudo tee /etc/apt/sources.list.d/libdvdcss.list
 sudo apt-get update
 sudo apt-get install libdvdcss2
```
Then with a  Successful install again run this in the terminal
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
  Rebooting may be necessary.
  After this, VLC will automatically use it with your DVD's.
Kind regards

---

### Post by Paul_Alexander on 2016-02-26
Thanks very much. I ran this without errors and can now play a DVD via VLC Player.
This page seemed legit, but I guess I should not have trusted it.[http://howtoubuntu.org/how-to-play-a-dvd-in-ubuntu](http://howtoubuntu.org/how-to-play-a-dvd-in-ubuntu) 

```
sudo /usr/share/doc/libdvdread4/install-css.sh

--2016-02-26 16:09:46--  http://download.videolan.org/pub/debian/stable//Packages
Resolving download.videolan.org (download.videolan.org)... 2a01:e0d:1:3:58bf:fa02:c0de:5, 88.191.250.2
Connecting to download.videolan.org (download.videolan.org)|2a01:e0d:1:3:58bf:fa02:c0de:5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520 (3.4K) [application/octet-stream]
Saving to: ‘/tmp/dvdcss-93UUf7/Packages’

100%[=======================================================>] 3,520       --.-K/s   in 0s      

2016-02-26 16:09:47 (7.47 MB/s) - ‘/tmp/dvdcss-93UUf7/Packages’ saved [3520/3520]

--2016-02-26 16:09:47--  http://download.videolan.org/pub/debian/stable/stable/libdvdcss2_1.2.13-0_amd64.deb
Resolving download.videolan.org (download.videolan.org)... 2a01:e0d:1:3:58bf:fa02:c0de:5, 88.191.250.2
Connecting to download.videolan.org (download.videolan.org)|2a01:e0d:1:3:58bf:fa02:c0de:5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44462 (43K) [application/octet-stream]
Saving to: ‘/tmp/dvdcss-93UUf7/libdvdcss.deb’

100%[=======================================================>] 44,462       143KB/s   in 0.3s   

2016-02-26 16:09:48 (143 KB/s) - ‘/tmp/dvdcss-93UUf7/libdvdcss.deb’ saved [44462/44462]

Selecting previously unselected package libdvdcss2.
(Reading database ... 210694 files and directories currently installed.)
Preparing to unpack .../dvdcss-93UUf7/libdvdcss.deb ...
Unpacking libdvdcss2 (1.2.13-0) ...
Setting up libdvdcss2 (1.2.13-0) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
```

---

