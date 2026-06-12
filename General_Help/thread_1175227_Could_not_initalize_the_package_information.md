---
title: "Could not initalize the package information"
date: 2009-05-31
forum: General Help
---

### Post by PaulTR on 2009-05-31
[http://i4.photobucket.com/albums/y102/paultr/Screenshot.png](http://i4.photobucket.com/albums/y102/paultr/Screenshot.png)

Problem showed up after following something on how to install Skype. Just curious as to how to fix this so I can access my manager again and install programs. Apt-get installs return:
E: Type '--09:44:12--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

thanks

---

### Post by drs305 on 2009-05-31
This may look serious but it's probably a very easy fix. The first (at least) line of your sources.list has an error. Post it here and we can figure it out:

```

cat /etc/apt/sources.list

```

More than likely you will just have to delete the first line. Instead of deleting, you could also just place a # symbol at the start of the line. Note: If the line doesn't start with either "deb" or a # symbol it is an error. 

To edit the file:
```

gksudo gedit /etc/apt/sources.list

```
Make the change, save the file, then:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by Soul-Sing on 2009-05-31
the last command above:
```
[sudo apt-get update && sudo apt-get upgrade
```

should be:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by PaulTR on 2009-06-01
paul@paul-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

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
deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) hardy main



that's the output from the file. I tried adding a pound sign in front of the first unpounded line, but it doesn't do anything.

---

### Post by michy99 on 2009-06-01
What about the output of:
```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by PaulTR on 2009-06-01
paul@paul-laptop:~$ cat /etc/apt/sources.list.d/medibuntu.list
--09:44:12--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `hardy.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 276 [text/plain]

    0K                                                       100%   26.00 MB/s

09:44:13 (26.00 MB/s) - `hardy.list' saved [276/276]

---

### Post by drs305 on 2009-06-01
PaulTR,

I didn't notice it was not your sources.list file, which looks fine, but your medibuntu file which is causing the problem.

See if you can open it with the following:

```

gksudo gedit /etc/apt/sources.list.d/medibuntu.list

```

If you are running jaunty, this is what it should look like. If intrepid or hardy, just replace "jaunty" with the appropriate entry. If you want to receive updates to the source code repository, uncomment the last line:
> 
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #Medibuntu - Ubuntu 9.04 "jaunty jackalope"
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #Medibuntu (source) - Ubuntu 9.04 "jaunty jackalope"


---

### Post by michy99 on 2009-06-01
This file is all messed up. It should look like this:

```
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free #Medibuntu - Ubuntu 8.04 "hardy heron"
deb-src http://packages.medibuntu.org/ hardy free non-free #Medibuntu (source) - Ubuntu 8.04 "hardy heron"
```

Edit: I see drs305 beat me to it. My version assumes you are on hardy 8.04 from your sources.lst you posted before.

---

### Post by PaulTR on 2009-06-01
Awesome, that worked out fine. Thanks :)

---

