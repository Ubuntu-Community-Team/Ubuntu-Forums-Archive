---
title: "Installing complete debian 7.4.6 [full installation]"
date: 2014-04-15
forum: Debian
---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-15
Hello i am muhammad ahmad mujtaba  and i am new to debian (pure) although i am using linux mint debian edition & Ubuntu 13.10 right now!


  [actually i have found LMDE very powerful and stable release there i decided to download and install debian operating system].
  Through official resources i have downloaded following images of debian operating system. Complete operating system image with updates.


  debian-7.4.0-amd64-DVD-1.iso,
debian-7.4.0-amd64-DVD-2.iso,
debian-7.4.0-amd64-DVD-3.iso,
debian-update-7.4.0-amd64-DVD-1.iso and
debian-update-7.4.0-amd64-DVD-2.iso.


  but now i'm confused how to make a bootable pendrive with all .iso images.
I have 4GB pendrive which i think isn't enough live pendrive image of debian.


  I have confusion that what should i do? Should i prepare the only bootable of only first image ie 'debian-7.4.0-amd64-DVD-1.iso' and after installing debian [ if possible anyhow ] and then somehow install all left images and updates.
  any help would be appreciated thanks!
  P.S. i know it's not about Ubuntu but it's about installing Linux and  i found askubuntu.org and ubuntuforums.com much active than any other  forums therefore, i am posting it here.

---

### Post by Olav on 2014-04-15
Hello, nice to see a Debian question here. Of course there is always [http://forums.debian.net/](http://forums.debian.net/) as well.

With Debian, the best (most practical/flexible) way to install is usually to use the netinst.iso which is only a small image (a few hundred MB). With that you can install a minimal operating system that is capable of booting and it lets you select the network mirrors from which you can download and install any additional packages that you might want. Of course if the computer on which you want to install does not have a network connection, it does not work so well and you may indeed need to use the DVD images. If you do need to use the DVD images, each image goes on a separate disk or thumb drive. It may be possible to combine more than one image on a single medium, but I am not aware of a way to do it.

The first DVD in the set contains most of the most popular packages. Depending on what you want, it is possible that you do not need any other disks in the set.

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-15
yeah thanks that is a good option but i have an offline PC, i may install Debian via net-install method on the PC and place all images over there but can i mount all images at a time like on Windows OS , i used to use Daemon Tools to mount more than one images as virtual DVD-rom's simultaneously , can i achieve this on Ubuntu 13.10 too or on Linux Mint Debian Edition?

---

### Post by sandyd on 2014-04-15
**Moved to other os/distro support**

---

