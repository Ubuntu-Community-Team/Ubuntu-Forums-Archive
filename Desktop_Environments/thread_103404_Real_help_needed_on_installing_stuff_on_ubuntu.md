---
title: "Real help needed on installing stuff on ubuntu"
date: 2005-12-14
forum: Desktop Environments
---

### Post by ikki_72 on 2005-12-14
i'd ask this stuff on a few threads, but no legitimate answer since i'd no internet access at home. there's any way i could do it e.g:download/copy n paste? try the xine first.

---

### Post by cvmostert on 2005-12-14
if you want to install xine....

sudo apt-get install xine

as easy as that
cheers

---

### Post by cvmostert on 2005-12-14
if you have no access, copy the file to the pc and

dpkg -i the_downloaded_xine_file.deb

---

### Post by kaamos on 2005-12-14
Ok, on you ubuntu without internet, open a terminal and type:
```
sudo apt-get install xine-ui
```
Then write down what packages would get installed. Then go somewhere where you have internet access and download the packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Then move them to a usb-stick or burn to a cd or something, and insert it to the ubuntu machine. Then open nautilus and navigate to /media/ and look for the folder that contains those files you brought. cdrom is in /media/cdrom and usb-stick is usually in /media/usbdrive. Once you find the .deb files, open a terminal and type:
```
sudo dpkg -i /media/**the_folder_where_they_are**/*.deb
```

Hope this helps! If you have problems, let us know.

---

### Post by ikki_72 on 2005-12-14
thanks dude, ur da best.:p

---

### Post by ikki_72 on 2005-12-16
1ST SITUATION:
i tried to install xine since i can't play mp3 on any default player. here's what happened:

x@ubuntu:~$ cd ~/Desktop/files
x@ubuntu:~/Desktop/files$ dir
MPlayer-1.0pre7try2.tar.bz2  lame-3.97b2.tar.gz
binutils-2.11.2.tar.gz       nvutut-0.3b.xpi
essential-20050412.tar.bz2   sbootmgr.dsk
flickrfs-1.0.tar.gz          xgetimage-xpatch-1.0.0.tar.bz2
fuse-2.4.2.tar.gz            xine
fwnes151.tgz                 zsnes-cvs_cvs-20050927-1_i386.deb
gcc-2.95.3                   zsnescvs20050927.tar.gz
gcc-2.95.3.tar.gz
x@ubuntu:~/Desktop/files$ cd gcc-2.95.3
x@ubuntu:~/Desktop/files/gcc-2.95.3$ ./configure
Configuring for a i686-pc-linux-gnuoldld host.
Created "Makefile" in /home/x/Desktop/files/gcc-2.95.3
/tmp/cONf8417.pos: line 7: cc: command not found
*** The command 'cc -o conftest -g   conftest.c' failed.
*** You must set the environment variable CC to a working compiler.
x@ubuntu:~/Desktop/files/gcc-2.95.3$

how i'm supposed to do? what i needed to do/downloads before i can compile it? fyi, i'm very new to linux n i don't have internet at home. usually i had to go to cc to surf internet.

2ND SITUATION:
downloaded /home/x/Desktop/files/mplayer-386_1.0-pre7cvs20050716-0.1ubuntu9_i386.deb, 'dpkg -i' it but errors popped out. something can't be build or it's like something is missing

---

### Post by ikki_72 on 2005-12-28
anyone?:KS

---

### Post by Perfect Storm on 2005-12-28
you are properly run into dependency problems. The applications (programs) you want to install needs other packages. This is a problem when you don't have internet.

---

### Post by ikki_72 on 2005-12-29
tell me something that i don't know:rolleyes:

---

### Post by Bartender on 2006-01-09
I tried the command kaamos described :

~$ sudo apt-get install samba-ui
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package samba-ui

This was with the machine offline of course.  I was hoping to see a list of the packages it would want so I could experiment with getting those and importing them somehow.  So I'm back to square one.

Is this operator error, or somethign wrong with computer, or is the "-ui" addition not correct for asking Synaptics what it would get?

---

