---
title: "Video problems in XFCE"
date: 2010-01-19
forum: Desktop Environments
---

### Post by joffu on 2010-01-19
Hi.
I have done a minimal ubuntu install and added xfce by loosely following this article:

[http://distrowatch.com/weekly.php?issue=20090504#feature]("http://distrowatch.com/weekly.php?issue=20090504#feature")

Basically...

-Installed Ubuntu 9.10 command line system from alternate cd.

-$ sudo apt-get install xorg xfce4 xfce4-goodies xubuntu-default-settings

(Use sliM instead of gdm)

-wget [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/slim/slim_1.3.1-4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/slim/slim_1.3.1-4_i386.deb)
sudo dpkg -i slim_1.3.1-4_i386.deb

I now have a very fast basic xubuntu install (on a 5 year old laptop - intel celeron with 512mb RAM).

My problem is the graphics. The display is slower than when I installed a normal ubuntu/xubuntu install, and the edges of icons etc. are rough. After googling a bit, I tried:
[I]
$ lspci | grep VGA
[/I]
which told me:

00.02,0 VGA compatible controller: Intel Corporation Mobile 915M/GMS/910GML Express Graphics Controller (rev 03)

Checking Xorg.conf revealed the "intel" driver was being used.

Following the advice from another website, I tried:

gksudo displayconfig-gtk

But nothing happens.

What am I missing? Are there other packages I need to install? (bearing in mind that I am pleased with performance now, and don't want to add too much more 'bloat').

Any help greatly appreciated.

---

