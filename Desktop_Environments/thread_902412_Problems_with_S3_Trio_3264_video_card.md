---
title: "Problems with S3 Trio 32/64 video card"
date: 2008-08-27
forum: Desktop Environments
---

### Post by Scunge on 2008-08-27
Sorry, I know there is an almost-directly relevant topic [**[color=blue]here[/color]**](http://backports.ubuntuforums.com/showthread.php?t=816679), but when I try to post a reply to that, it keeps on asking me for my login details, and despite ticking the "Remember me" box, it never lets me post. Maybe the tread's locked or something, but then why would I get a "Post reply" option?

Anyway... I've started this new topic here instead.

I have similar problems with an old S3 display card (Windows identifies it as an "*S3 Trio 32/64*").

It doesn't scroll window contents properly if I use the automatically-setup "s3" in xorg.xonf, and as suggested by some other topics here I had to change the driver to "vesa" and 16 bit colour depth to get anything usable. Even then, it's soooo slow even on a 700 MHz machine, you can see it drawing every part of every window.

However, in trying to follow Shismaeroth's advice in the (current) last post in that other topic, I'm afraid I don't get very far at all!

> launch "kcmshell"
I get the following:
```
$ kcmshell
The program 'kcmshell' is currently not installed.  You can install it by typing:
sudo apt-get install kdelibs4c2a
bash: kcmshell: command not found

$ sudo apt-get install kdelibs4c2a
[...]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  kdelibs-data libarts1c2a libartsc0 libavahi-qt3-1 liblua50 liblualib50
  libqt3-mt
Suggested packages:
  fam perl-suid libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql
Recommended packages:
  libarts1-akode
The following NEW packages will be installed
  kdelibs-data kdelibs4c2a libarts1c2a libartsc0 libavahi-qt3-1 liblua50
  liblualib50 libqt3-mt
[...]
Get: 1 http://gb.archive.ubuntu.com hardy-backports/main kdelibs-data 4:3.5.10-0ubuntu1~hardy1 [7326kB]
Get: 2 http://gb.archive.ubuntu.com hardy-backports/main libartsc0 1.5.10-0ubuntu1~hardy1 [15.7kB]
Get: 3 http://gb.archive.ubuntu.com hardy/main libqt3-mt 3:3.3.8-b-0ubuntu3 [3299kB]
Get: 4 http://gb.archive.ubuntu.com hardy-backports/main libarts1c2a 1.5.10-0ubuntu1~hardy1 [1071kB]
Get: 5 http://gb.archive.ubuntu.com hardy/main libavahi-qt3-1 0.6.22-2ubuntu4 [33.4kB]
Get: 6 http://gb.archive.ubuntu.com hardy/main liblua50 5.0.3-3 [48.7kB]       
Get: 7 http://gb.archive.ubuntu.com hardy/main liblualib50 5.0.3-3 [35.1kB]    
Get: 8 http://gb.archive.ubuntu.com hardy-backports/main kdelibs4c2a 4:3.5.10-0ubuntu1~hardy1 [9614kB]
[...]
Selecting previously deselected package ...
Unpacking ...
[All did this with no other messages shown]

Setting up ...
[All did this with no other messages shown]

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

$ kcmshell
kbuildsycoca running...
Usage: kcmshell [Qt-options] [KDE-options] [options] module 

A tool to start single KDE control modules

[List of options excluded]

$ kcmshell --list
kbuildsycoca running...
Reusing existing ksycoca
The following modules are available:

$ 


```

I've left in certain package information so you can see exactly what was installed.

What exactly is the *kcmshell* command you are suggesting is run?

Thanks in advance.

---

### Post by overdrank on 2008-08-27
Hi and try this link 
[http://ubuntuforums.org/showthread.php?t=816679&highlight=Problems+xorg.conf%2C+PCI+S3+ViRGE&page=2](http://ubuntuforums.org/showthread.php?t=816679&highlight=Problems+xorg.conf%2C+PCI+S3+ViRGE&page=2)

Have no idea where the backports came from in your link.

---

### Post by Scunge on 2008-08-27
Thanks. I've reposted in that thread, you can delete this one if you like.

> Have no idea where the backports came from in your link.
I couldn't narrow down the search enough directly on the forums here, so I did a [**[color=blue]Google search[/color]**](http://www.google.co.uk/search?hl=en&q=Problems+with+xorg.conf%2C+PCI+S3+ViRGE+site%3A+backports.ubuntuforums.com&btnG=Search&meta=); that link is somewhat fixed, but shows you the use of "backports" in the URL.

---

