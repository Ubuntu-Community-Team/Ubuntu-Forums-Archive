---
title: "Playing Video"
date: 2006-02-04
forum: Desktop Environments
---

### Post by Monkey12 on 2006-02-04
I cannot seem to play any videos in common formats such as MPEG, AVI, or WMV. I have tried installing the w32 codecs as explained in the wiki, but I still can't seem to get it to work. Thanks ahead of time for any help.

---

### Post by jesus_pereira on 2006-02-04
Open your sources.list

$ sudo gedit /etc/apt/sources.list

Add this lines

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

Make 

$ sudo apt-get update

and

$ sudo apt-get install w32codecs  libdvdcss2 

See too: [http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?t=1171&highlight=plf]("http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?t=1171&highlight=plf")


Too:

$ sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-lame gstreamer0.8-ffmpeg lame sox ffmpeg mjpegtools gstreamer0.8-pitfdll mpg321

See too:
[http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?t=1083]("http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?t=1083")

---

### Post by Monkey12 on 2006-02-06
Thanks for the help, but it didn't seem to work. Do I need to do anything inside of totem to tell it what codecs to use?

---

### Post by adi-beg on 2006-02-06
I had a lot of same problems. I solved them with installing vlc and mplayer. I used automatix to achieve this. Mplayer works as plugin inside firefox and plays windows media files, while vlc works as dvd player.

---

### Post by adi-beg on 2006-02-06
There is one more issue. If you get a message like this:

```
libdvdread: Invalid IFO for title 2 (VTS_02_0.IFO).
Cannot open the IFO file for DVD title 2.
```

it means that you have to install regionset and run it to change region code of your dvd player (for those players libdvdcss2 has no effect, you have to change code first). But be aware that you can change code up to five times. After that it will be locked on the last change you have made.

---

### Post by adi-beg on 2006-02-06
I had a thread some time ago: [http://www.ubuntuforums.org/showthread.php?t=122940]("http://www.ubuntuforums.org/showthread.php?t=122940")

Maybe it will help...

---

### Post by Supertip on 2006-02-07
if i could read it....

---

### Post by Monkey12 on 2006-03-01
[QUOTE=jesus_pereira]Open your sources.list

$ sudo gedit /etc/apt/sources.list

Add this lines

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

Make 

$ sudo apt-get update

and

$ sudo apt-get install w32codecs  libdvdcss2 

See too: [http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?t=1171&highlight=plf]("http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?t=1171&highlight=plf")


Too:

$ sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-lame gstreamer0.8-ffmpeg lame sox ffmpeg mjpegtools gstreamer0.8-pitfdll mpg321

See too:
[http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?t=1083]("http://www.linuxval.org/ubuntu/phpBB2/viewtopic.php?t=1083")[/QUOTE]

I tried this, and this is what I got.

Reading package lists... Done
Building dependency tree... Done
w32codecs is already the newest version.
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by Perfect Storm on 2006-03-01
Ummm....are you using breezy or hoary, you might have mixed up your sourcelist if you're using breezy.

If you are using breezy check my sourcelist:

> deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse


## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

## Backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

## Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## PLF testing package
deb [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free

Where it says dk, change it to your country code or a place closer to you.

---

### Post by Monkey12 on 2006-03-01
I'm still pretty new to linux so i'm not completely sure, but everything in my source list has hoary in it so I think i'm using hoary.

---

### Post by Perfect Storm on 2006-03-01
Find the "About Gnome" in the tabs. Does it say Version: 2.12.1 or Version 2.10.x

---

### Post by Monkey12 on 2006-03-01
2.12.1

---

### Post by Perfect Storm on 2006-03-01
Then it's breezy you have.

---

### Post by Monkey12 on 2006-03-01
I'm sorry, i'm still not sure what I need to add/remove/change in my source list. Mine is very different from yours. Here is my source list.

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-securg lity main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by Perfect Storm on 2006-03-01
Erease the old one and add everything. The only thing you need is change my dk to us. Then you have all what you need.

You may not want these
## PLF testing package
deb [http://antesis.freecontrib.org/mirro.../devnotpublic/](http://antesis.freecontrib.org/mirro.../devnotpublic/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirro.../devnotpublic/](http://antesis.freecontrib.org/mirro.../devnotpublic/) breezy free non-free

as they are for testing PLF stuff.

remember after save an exit the sourcelist you have to do:
```
sudo apt-get update
```

---

