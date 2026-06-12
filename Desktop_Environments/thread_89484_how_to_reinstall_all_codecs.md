---
title: "how to reinstall all codecs?"
date: 2005-11-12
forum: Desktop Environments
---

### Post by forlog on 2005-11-12
Hi,

I've installed some codecs (like w32codecs) but I cannot install anything alse - I'm getting error messages saying that package "xxxxx" is not installable. How can I uninstall everything and install again in the right order(?)  ???

---

### Post by Xian on 2005-11-12
[QUOTE=forlog]Hi,

I've installed some codecs (like w32codecs) but I cannot install anything alse - I'm getting error messages saying that package "xxxxx" is not installable.[/QUOTE]
You generally get that error message because you have not added the needed repository to install the desired package. It might help if you were to post the exact error message so this can be confirmed.

[How-To Install Extra Repos](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse).

---

### Post by forlog on 2005-11-12
This is my sources.list:
```


deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 

deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted 

deb http://archive.ubuntu.com/ubuntu/ breezy universe 
deb-src http://archive.ubuntu.com/ubuntu/ breezy universe 

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu/ breezy-security universe 
deb-src http://security.ubuntu.com/ubuntu/ breezy-security universe 

deb http://archive.ubuntu.com/ubuntu/ breezy multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ breezy multiverse 

deb http://archive.ubuntu.com/ubuntu/ warty universe 
deb-src http://archive.ubuntu.com/ubuntu/ warty universe 
deb http://archive.ubuntu.com/ubuntu/ warty multiverse 


```

---

### Post by Xian on 2005-11-12
Add this entry to your sources.list then 'apt-get update'.

```
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free
```

---

### Post by forlog on 2005-11-12
I did it but still have problems. When I try to install ffmpeg such message is shown:
```

ffmpeg:
 Requires: libdc1394-13  but it is not installable
 Requires: libimlib2  but it is not installable

```
and I cannot find those packages.

Why there is so much repositories? One repository with mirrors would be more convenient - like portage of gentoo :D

---

### Post by CyiPherX on 2005-11-12
[QUOTE=forlog]I did it but still have problems. When I try to install ffmpeg such message is shown:
```

ffmpeg:
 Requires: libdc1394-13  but it is not installable
 Requires: libimlib2  but it is not installable

```
and I cannot find those packages.

Why there is so much repositories? One repository with mirrors would be more convenient - like portage of gentoo :D[/QUOTE]

Have a look at this post that i just made [http://ubuntuforums.org/showthread.php?t=89417](http://ubuntuforums.org/showthread.php?t=89417)

Hopefully that will help you out.

One of the things i like about this forum is that 99% of the things that you try to do in Linux, someone else as also tried to do it, and the information is all here .

CyiPherX:smile:

---

### Post by Treebeard on 2005-11-12
You can find a usefull (unofficial) repository on [http://debian.video.free.fr/](http://debian.video.free.fr/)
for multimedia stuff.

Cheers

---

### Post by Xian on 2005-11-12
[QUOTE=forlog]I did it but still have problems. When I try to install ffmpeg such message is shown:
```

ffmpeg:
 Requires: libdc1394-13  but it is not installable
 Requires: libimlib2  but it is not installable

```
and I cannot find those packages.

Why there is so much repositories? One repository with mirrors would be more convenient - like portage of gentoo :D[/QUOTE]

These packages are in the main Ubuntu repositories. 
You don't need any extra repo entries in order to access them.

```
# apt-cache policy libimlib2
libimlib2:
  Installed: 1.2.0-2.2ubuntu2
  Candidate: 1.2.0-2.2ubuntu2
  Version table:
 *** 1.2.0-2.2ubuntu2 0
        500 http://archive.ubuntu.com breezy/main Packages
        100 /var/lib/dpkg/status

# apt-cache policy libdc1394-13
libdc1394-13:
  Installed: 1.1.0-2
  Candidate: 1.1.0-2
  Version table:
 *** 1.1.0-2 0
        500 http://archive.ubuntu.com breezy/main Packages
        100 /var/lib/dpkg/status
```

---

### Post by forlog on 2005-11-14
Thanks! I don't know why but now everything seems to be ok.

---

