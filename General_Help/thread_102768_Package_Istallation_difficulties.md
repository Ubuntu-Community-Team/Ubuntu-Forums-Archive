---
title: "Package Istallation difficulties"
date: 2005-12-12
forum: General Help
---

### Post by likedude15 on 2005-12-12
i am having trouble installing a clamav package on my comp...it says it need different libraries but when i go download those...the are not installable either....what can i do?


chris palmer

---

### Post by inhetep on 2005-12-12
Did you use apt-get? If not this should do the trick

```

sudo apt-get install clamav
```

---

### Post by likedude15 on 2005-12-12
yes and it came up with the librarie that cant be installed


chris

---

### Post by inhetep on 2005-12-12
I guess u have unlocked all respositories.

Which library is it?

---

### Post by likedude15 on 2005-12-12
here are the ones

The following packages have unmet dependencies:
  clamav: Depends: libclamav1 (>= 0.83) but it is not going to be installed
               Depends: libgmp3 but it is not installable

and what are youtalking repositories?

chris

---

### Post by inhetep on 2005-12-12
in simple terms, respositories are the place where ubuntu packages are stored on the internet.
Usually not all respositories are activated by default, e.g. the universe resp.

This should help you if u use synaptic:

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)


If u use apt-get please this will help u
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

and then it should look like this

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse 



save the file

and make 

```
sudo apt-get update
```

and try again

```
sudo apt-get install clamav
```

---

### Post by likedude15 on 2005-12-12
alright,

didnt work...it is giving me the same message with new saying broken packages...

chris

---

### Post by inhetep on 2005-12-13
As it seems libgmp3 has been replaced by  libgmp3c2.

This is a last try, if it doesn't work file a bug report ([https://bugzilla.ubuntu.com/)](https://bugzilla.ubuntu.com/)).

try to install libgmp3c2 

```
sudo apt-get install libgmp3c2
```

and then try to install clamav again.

Alternatively if you need a virus scanner try 

[http://www.bitdefender.com/](http://www.bitdefender.com/)
[http://www.avast.com/eng/programs.html](http://www.avast.com/eng/programs.html)
[http://www.grisoft.com/doc/Programs/lng/us/tpl/tpl01](http://www.grisoft.com/doc/Programs/lng/us/tpl/tpl01)
[http://www.free-av.com/](http://www.free-av.com/)
[http://www.f-prot.com/products/home_use/linux/](http://www.f-prot.com/products/home_use/linux/)
[http://www.amavis.org/](http://www.amavis.org/)


or try to compile clamav using the sources


[http://sourceforge.net/project/showfiles.php?group_id=86638&release_id=368319](http://sourceforge.net/project/showfiles.php?group_id=86638&release_id=368319)

---

