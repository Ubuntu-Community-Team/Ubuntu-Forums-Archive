---
title: "ubuntu repositories problem...URGENT !!!!"
date: 2009-06-14
forum: General Help
---

### Post by jasim.home on 2009-06-14
I installed ubuntu 9.04 inside windows xp(ubuntu cd 9.04), then install package using repositories DVD (dvd Ubuntu-9.04-i386.iso). I DONT HAVE INTERNET.
at first some times i installed some package from synaptic but after rebooting or doing somethig else synaptic cannot detect my repository dvd.

here is some error i get from synaptic>reload...(by marking package)
```
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```[IMG]http://img7.imageshack.us/img7/4461/53081984.png[/IMG]

/etc/apt/sources.list.save   (source list file .. )

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)]/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

```Please help me quickly...sorry for my bad english :(

---

### Post by Soul-Sing on 2009-06-14
disble the .deb cdrom both in software sources, as in your sources.list: 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.3)]/ jaunty

---

### Post by jasim.home on 2009-06-14
i disabled and then insert the dvd again...Nothings happens..:((

---

### Post by jasim.home on 2009-06-14
I have to install package from dvd (ubuntu-9.04-i386.iso) instead downloading from internet. ANY SOLUTION?
 :-s

---

### Post by ramnarayan on 2009-06-14
> **jasim.home said:**
> I have to install package from dvd (ubuntu-9.04-i386.iso) instead downloading from internet. ANY SOLUTION?
 :-s

copy the dvd to an hd location

add the following line to your sources.list (/etc/apt/sources.list)

deb file:///location_foo/locationfoo/jaunty_dvd/ jaunty main multiverse universe 

(location_foo being the location where you copy your dvd - the directory should have dist and pool directories inside

***
Example from my Gutsy Gibbon repositories are - the directory structure is as below

/media/sda7/gibbon5
/media/sda7/gibbon5/dists
/media/sda7/gibbon5/pool

and the line in my sources.list reads

# adding 7.10 material transferred from dvd to usb disk
#gutsy gibbon 7.10
deb file:///media/sda7/gibbon5/ gutsy main multiverse universe 

***
this has worked very well for me 

ram

---

### Post by ramnarayan on 2009-06-14
[QUOTE=ramnarayan;7456315]copy the dvd to an hd location

I think you may have to extract the iso so that you can see its directories

- the dvd's i have were repo dvd's not iso's

ram

---

### Post by ugm6hr on 2009-06-14
Perhaps you could try what it advises?  I don't use CDs, but it should be easy to try this:

```
apt-cdrom add
```

Then make sure the CD is in the tray.

Then try installing.

---

### Post by jasim.home on 2009-06-14
> **ugm6hr said:**
> Perhaps you could try what it advises?  I don't use CDs, but it should be easy to try this:

```
apt-cdrom add
```Then make sure the CD is in the tray.

Then try installing.

RESULT: 
```
apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Failed to mount the cdrom.

```

---

### Post by ugm6hr on 2009-06-14
> **jasim.home said:**
>  
```
E: Failed to mount the cdrom.

```

This seems to be the problem.

Can you access the files on the CD at all?

---

### Post by jasim.home on 2009-06-14
> **ramnarayan said:**
> copy the dvd to an hd location

add the following line to your sources.list (/etc/apt/sources.list)

deb file:///location_foo/locationfoo/jaunty_dvd/ jaunty main multiverse universe 

(location_foo being the location where you copy your dvd - the directory should have dist and pool directories inside

***
Example from my Gutsy Gibbon repositories are - the directory structure is as below

/media/sda7/gibbon5
/media/sda7/gibbon5/dists
/media/sda7/gibbon5/pool

and the line in my sources.list reads

# adding 7.10 material transferred from dvd to usb disk
#gutsy gibbon 7.10
deb file:///media/sda7/gibbon5/ gutsy main multiverse universe 

***
this has worked very well for me 

ram

i did all as you said but it dosen't work...:(
two new error:
[IMG]http://img33.imageshack.us/img33/4179/67952860.png[/IMG]

THEN AFTER CLOSING THIS

[IMG]http://img33.imageshack.us/img33/1677/96714327.png[/IMG]

:(

---

### Post by Soul-Sing on 2009-06-14
maybe this will be helpul: [http://ubuntuforums.org/showthread.php?t=837209](http://ubuntuforums.org/showthread.php?t=837209)

---

### Post by jasim.home on 2009-06-14
> **ugm6hr said:**
> This seems to be the problem.

Can you access the files on the CD at all?
of course, i copied whole dvd for testing ramnarayan's trick.

please read my first  post carefully that at first mounting dvd i installed some package..
```

Commit Log for Sat Jun 13 11:39:07 2009


Installed the following packages:
dkms (2.0.21.1-0ubuntu3)
fakeroot (1.12.1ubuntu1)
nvidia-180-kernel-source (180.44-0ubuntu1)
nvidia-180-libvdpau (180.44-0ubuntu1)
nvidia-glx-180 (180.44-0ubuntu1)
nvidia-settings (180.25-0ubuntu1)
patch (2.5.9-5)
```


_**@ramnarayan**_

when i tried to reload synaptic package manager..

```
Failed to fetch file:/media/JASIM'S/jaunty_dvd/dists/jaunty/Release  Unable to find expected entry  multiverse/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

```

OH...I GOT SOME PACKAGE THERE, 
_**MAIN & RESTRICTED.**_
IT WORKED FINALLY ( I have to see more...may be tomorrow)
Thanks.
***i dont have any multiverse file/folder in my dvd.

---

### Post by jasim.home on 2009-06-14
bug!. . . i have to sleep noww...:(

---

### Post by ramnarayan on 2009-06-15
> **jasim.home said:**
> of course, i copied whole dvd for testing ramnarayan's trick.
_**@ramnarayan**_

when i tried to reload synaptic package manager..

```
Failed to fetch file:/media/JASIM'S/jaunty_dvd/dists/jaunty/Release  Unable to find expected entry  multiverse/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

```

OH...I GOT SOME PACKAGE THERE, 
_**MAIN & RESTRICTED.**_
IT WORKED FINALLY ( I have to see more...may be tomorrow)
Thanks.
***i dont have any multiverse file/folder in my dvd.

Just curious did the method i suggested work, and if so was the failure part because the multiverse was not there in the extracted ISO.

Also if you issue is solved maybe you can edit the title and put (SOLVED) at the end.

regards
ram

---

