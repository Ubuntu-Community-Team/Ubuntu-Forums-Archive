---
title: "Ubuntu Lame Help"
date: 2006-05-25
forum: Desktop Environments
---

### Post by JohnN on 2006-05-25
Hello, Everbody...


Does anyone here know where I get the liblamemp3.so.0 file?


I am trying to export an audio file as a mp3 file.

I have tried to search the internet, and tryed to install it via the mp3dev.org website also.

Please help me!


Have a blssed day

---

### Post by aysiu on 2006-05-25
There are two things at issue here.

One, [you need the proper codecs installed](https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970).

Two, you need to find that file. Audacity will look for liblamemp3.so.0 in /usr/lib, but you actually want to select liblamemp3.so.0.0

---

### Post by JohnN on 2006-05-25
I have already tried that along time ago.

I have almost gstreamer 0.8 mad on my system, along with all the items that came up for "lame" in synaptic, with all the sources checked (where they all combined equal out to 17350) 

What else could I try?

---

### Post by aysiu on 2006-05-25
You tried looking for *all files* in /usr/lib instead of just for that specific one? Can I assume you're using Audacity?

---

### Post by JohnN on 2006-05-25
Yes, I am using Audacity in Ubuntu 5.10.

I have tried search for it using the search for files program under "Places"  using liblame*.* and liblame*.*.* searching the filesystem and found nothing.

---

### Post by JohnN on 2006-05-29
Can Anyone out there help me with this?

---

### Post by aysiu on 2006-05-29
Can you post the output of these commands? ```
cat /etc/apt/sources.list
sudo aptitude update
sudo aptitude install liblame0 lame lame-extras glame gstreamer0.8-lame
cat /etc/apt/sources.list
sudo updatedb
locate liblame
``` Note: that second-to-last command may take a few minutes to complete.

---

### Post by JohnN on 2006-05-29
Sure, just did that and the commands are as follows, (its long)

john@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
john@ubuntu:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release [19.6kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [62.8kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages [39.0kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources [18.6kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [17.7kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources [5185B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [35.7kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources [14B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources [10.2kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources [701B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Fetched 320kB in 11s (27.5kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
john@ubuntu:~$ sudo aptitude install liblame0 lame lame-extras glame gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
Couldn't find any package whose name or description matched "liblame0"
No candidate version found for lame
No candidate version found for lame-extras
Couldn't find any package whose name or description matched "gstreamer0.8-lame"
The following packages have been kept back:
  python-pgsql python2.4-pgsql
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Reading task descriptions... Done
john@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
john@ubuntu:~$ sudo updatedb
fatal error: updatedb: create_db(): rename: Read-only file system
john@ubuntu:~$ locate liblame
/home/john/lamemp3/debian/liblame0.files
/home/john/lamemp3/debian/liblame0-dev.files
/home/john/lamemp3/debian/liblame0-dev.docs
/home/john/lame/debian/liblame0-dev.docs
/home/john/lame/debian/liblame0-dev.files
/home/john/lame/debian/liblame0.files

---

### Post by aysiu on 2006-05-29
It's weird that you got all those "no installation candidate" errors, since you can clearly see [here](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/) that the installation candidates are there.

Maybe comment out the CD-ROM source and try again...? "Comment out" means "put a # sign in front of that line in your /etc/apt/sources.list."

Also, that error you get after *sudo updatedb* looks worrisome.

---

### Post by bjorng on 2006-05-31
[QUOTE=JohnN]
john@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted **multiverse**
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted **multiverse**

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted **multiverse**
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted **multiverse**
[/QUOTE]

You need to add the string " multiverse" to the ends of the lines above that begin with "deb http://", then if you follow the steps you were given earlier, you'll get the components you need.  (It's not strictly needed on the deb-src lines, but it doesn't hurt to add them just in case.)

---

### Post by daojones on 2008-07-14
Hi Aysiu:

Thank you!  I don't know if you solved the problem for John, but your advice worked great for me.  I have been wrestling with the Lame issue for 2 days.  I never would have come up with the command line solution on my own.

Thanks again.
Dao

---

