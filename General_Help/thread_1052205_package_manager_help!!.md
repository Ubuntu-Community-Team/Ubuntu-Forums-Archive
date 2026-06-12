---
title: "package manager help!!"
date: 2009-01-27
forum: General Help
---

### Post by ibootindos on 2009-01-27
so I'm installing packages, and I got this error, can anybody help me out?


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'Error' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'


thanks for your help!

---

### Post by cosine352 on 2009-01-27
what does this file says?

> sudo gedit /etc/apt/sources.list

---

### Post by ibootindos on 2009-01-27
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by ibootindos on 2009-01-27
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://iq.archive.ubuntu.com/ubuntu/](http://iq.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by carolinason on 2009-01-27
What is the output of this command? ```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by ibootindos on 2009-01-27
rick@coolguy:~$ sudo -i
sudo: unable to resolve host coolguy
[sudo] password for rick: 
root@coolguy:~# cat /etc/apt/sources.list.d/medibuntu.list
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
root@coolguy:~#

---

### Post by carolinason on 2009-01-27
it appears that the package manager isn't pointing to the correct sources.list. I'm checking on it for you.

---

### Post by carolinason on 2009-01-27
try  ```
ls /etc/apt/sources.list.d/
```

---

### Post by ibootindos on 2009-01-27
rick@coolguy:~$ ls /etc/apt/sources.list.d/
hardy-partner.list  medibuntu.list
rick@coolguy:~$

---

### Post by carolinason on 2009-01-27
It seems mediubuntu wants to populate the sources to the directory /etc/apt/sources.list.d/ and not /etc/apt/sources.list, which appears to be fine to do so.

---

### Post by carolinason on 2009-01-27
sorry for the list of commands

what is the contents of the file hardy-partner.list medibuntu.list?```
cat /etc/apt/sources.list.d/hardy-partner.list
```

---

### Post by ibootindos on 2009-01-27
ok... so how do I adjust that?

---

### Post by ibootindos on 2009-01-27
rick@coolguy:~$ cat /etc/apt/sources.list.d/hardy-partner.list.medibuntu.list
cat: /etc/apt/sources.list.d/hardy-partner.list.medibuntu.list: No such file or directory
rick@coolguy:~$ 


sorry if my responses seem off, slow connection.

---

### Post by carolinason on 2009-01-27
the output of ls /etc/apt/sources.list.d/ seems be hardy-partner.list and medibuntu.list

these files must have correct synatx and i'd need to see these lists to check

---

### Post by ibootindos on 2009-01-27
rick@coolguy:~$ cat /etc/apt/sources.list.d/hardy-partner.list.medibuntu.list
cat: /etc/apt/sources.list.d/hardy-partner.list.medibuntu.list: No such file or directory
rick@coolguy:~$ 


sorry if my responses seem off, slow connection.

---

### Post by carolinason on 2009-01-27
cool, i just wanted to get on the same page

one of your outputs shows a space between hardy-partner.list **[COLOR="Blue"]and[/COLOR]** medibuntu.list are these two different files or a typo?

---

### Post by ibootindos on 2009-01-27
two different files. I copied the output exactly as is. I switched to the medibuntu source somehow, is there a way I could get off it and switch back to the regular multiverse or whatever I'm supposed to be on? would that help? I'm still learning. lol

---

### Post by carolinason on 2009-01-27
well symantic's repositories can be configured by opening it and go to settings -> repositories uncheck the offending repositories, which appear to be hardy-partner.list and medibuntu.list.

The problem also appears to be in one of these two files.

---

### Post by carolinason on 2009-01-27
i've never used the mediubuntu repos, so i'm not fully aware of how they work with symantic. i see that sources can exist in different dirstories and i assume that the syntax is the same for any source.list file. you should be able to continue to run medibunu, but we need to fix the sources.list

---

### Post by ibootindos on 2009-01-27
ok cool, how do we fix the source list? and if its a problem I can stop using medibuntu, if it makes this whole gig easier.

---

### Post by ibootindos on 2009-01-27
also I can't open the package manager without getting that orginal error.

---

### Post by carolinason on 2009-01-27
i need to see the cats of both sources.list. 
```

cat /etc/apt/sources.list.d/hardy-partner.list
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by dougfractal on 2009-01-27
sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.broken
sudo apt-get update

---

### Post by carolinason on 2009-01-27
> root@coolguy:~# cat /etc/apt/sources.list.d/medibuntu.list
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
root@coolguy:~#

looks like the first line in medibuntu.list is a url and it's incorrect.

---

### Post by oldos2er on 2009-01-27
Run
```
gksu gedit /etc/apt/sources.list.d/medibuntu.list
```
and add a comment mark # at the beginning of the first line. Then run
```
sudo apt-get update
```

 It also appears you have an error in one of your hosts files.

---

### Post by ibootindos on 2009-01-27
thanks, solved.

---

### Post by dubhear on 2009-04-20
> **ibootindos said:**
> rick@coolguy:~$ ls /etc/apt/sources.list.d/
hardy-partner.list  medibuntu.list
rick@coolguy:~$

well. did it work?

---

