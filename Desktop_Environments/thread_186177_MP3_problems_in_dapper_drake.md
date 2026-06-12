---
title: "MP3 problems in dapper drake"
date: 2006-06-01
forum: Desktop Environments
---

### Post by jonboy99 on 2006-06-01
Just installed kubuntu dapper drake tonight - fresh install.  Am trying to play mp3s using amarok.  Followed the instructions on [www.ubuntuguide.org](www.ubuntuguide.org) under the 'How to install Multimedia Codecs' section. 

This worked fine with breezy but in dapper when i press the play button after dragging the mp3 into amarok, there is no sound and it immediately comes up with 'playlist finished' as though it has played the track in a split second without any sound.
Otherwise it seems to act as though all is fine.

Any ideas?

Cheers
Jon.

---

### Post by zupermanz on 2006-06-01
I have the same problen too, i used the xine engine with no success. I cant configure arts. Mp3 play fine with xmms.
I have an amilo m7400 (centrino 1600 512M)

---

### Post by Turgon on 2006-06-01
Dapper uses the new 0.10 verison of gstreamer and therefor you cannot use the 0.8 plugins at the ubuntuguide.

To get mp3 and other formats going, you should try to search for gstreamer in synaptic and install the packages called something like:

Gstreamer 0.10-bad
gstreamer 0.10-ugly

Hope this works for you!

---

### Post by GoldBuggie on 2006-06-01
ubuntuguide.org is for breezy so some things wont work. I would look at something like [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page) instead.

but for your problem do a
```
sudo apt-get install libxine-extracodecs
```

---

### Post by zupermanz on 2006-06-01
I cant choose the gstreamer engine dont know why.


GoldBuggie----->When i sudo apt-get install libxine-extracodecs i get:
Package libxine-extracodecs is not available, but is referred to by another package

---

### Post by zupermanz on 2006-06-01
Anyway ive insatlled it from:
[http://packages.ubuntu.com/dapper/libs/libxine-extracodecs](http://packages.ubuntu.com/dapper/libs/libxine-extracodecs)

It works now...

Can i have a list of your repositories? (your apt-get file that is) because i think thats those that i use do not get updated fast

Thanks!

---

### Post by jonboy99 on 2006-06-01
Hi, also had the same problem with the libzine-extracodecs package.  However just used easyubuntu and all working well now.

[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

cheers
jon



PS anyone else having trouble with adept not loading roughly every 2 out of 3 attempts?  The egg time spins on the taskbar and then it closes itself.  Have done the update too - made no difference.

---

### Post by Rackerz on 2006-06-01
Also when installing codecs for MP3 etc it is best to use this page, it includes all the information for installing them on Dapper too;

[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28RestrictedFormats%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28RestrictedFormats%29)

Regards

---

### Post by jonboy99 on 2006-06-01
Hmm, although all the video formats are now working, they're all very choppy, especially in full screen.

---

### Post by Rackerz on 2006-06-01
[QUOTE=jonboy99]Hmm, although all the video formats are now working, they're all very choppy, especially in full screen.[/QUOTE]

By anychance are they wmv video?

---

### Post by jonboy99 on 2006-06-01
They're all from my windows installation - mpg, mpeg, wmv, avi and mov.  All choppy, but wmv probably best of the lot.  Not sure if that particular one i tried was lower bitrate or something though.

EDIT - choppy video problem fixed now, by choosing no to the enable kernel framebuffer mode when reconfiguring x with the 'sudo dpkg-reconfigure xserver-xorg' command.  I had answered yes to this after installing the ati driver, and hadn't tried playing videos before this.

---

### Post by Rackerz on 2006-06-01
It's probably the WMV's. All my AVI, MOV, MPG, MPEG run perfectly ;). Are you using totem?

EDIT: I just checked a few, one was choppy but the other wasn't. I guess it just depends on the file.

---

### Post by GoldBuggie on 2006-06-02
This is my sources.list (it is the "se" version mening from sweden)
```
deb http://kubuntu.org/packages/kde-353 dapper main
deb http://kubuntu.org/packages/amarok-latest dapper main

deb http://se.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb http://se.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

# deb http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

---

### Post by fornix on 2006-06-02
just remove all the # from anything tht looks like sources, lines starting with deb
then sudo 
```
sudo apt-get update
```
should do the trick. will find libxine-extracodecs

---

