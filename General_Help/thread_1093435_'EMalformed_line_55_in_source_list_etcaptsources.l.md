---
title: "'E:Malformed line 55 in source list /etc/apt/sources.list (URI),"
date: 2009-03-11
forum: General Help
---

### Post by Henery on 2009-03-11
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 55 in source list /etc/apt/sources.list (URI), E:The list of sources could not be read.'


This is the error I get I was installing my fingerprint reader and now messed things up anyone know how to fix this I am lost!

---

### Post by kanikilu on 2009-03-11
Can you post the contents of your /etc/apt/sources.list file?

---

### Post by Henery on 2009-03-11
```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Fingerprint reader support (fprint)
deb 
http://ppa.launchpad.net/madman2k/ubuntu hardy main restricted universe 

multiverse
```

there it is I think the error is in the last part of the lst what should I do delete the whole file?

---

### Post by Henery on 2009-03-11
Now I can't run update manager now it give's the same error I am screwed if I can't fix this! =no updates

---

### Post by kanikilu on 2009-03-11
Is that exactly how the file is? If so, the last line needs the extra line breaks removed: ```
deb http://ppa.launchpad.net/madman2k/ubuntu hardy main restricted universe multiverse
```

...although it's not line 55 :?:

---

### Post by yther on 2009-03-11
You'll need to edit the file and fix that last line.  Open a terminal and run:

```
gksu gedit /etc/apt/sources.list
```

(You have to use **gksu** because you won't have permission to save the changes if you don't.)

Go down to the bottom and rejoin the broken line so it looks like the others, as kanikilu said.  Then save the file, quit the editor, and try your update again.  :)

*Edit:  There sure have been a lot of people posting lately with mysteriously broken sources files... I wonder what is causing this... :?*

---

### Post by Henery on 2009-03-11
Hmm how do edit the file I do not have permission?

---

### Post by bodhi.zazen on 2009-03-11
use sudo if you are editing in a terminal (sudo nano ... or sudo -e /etc/apt/sources.list)

Or for a graphical editor ```
gksu gedit /etc/apt/sources.list
```

Also, for futrue referance :

```
cat -n /etc/apt/sources.list | grep ^55
```

It appears as if the last source, at the bottom, is broken into several lines when it should all be on one line.

---

### Post by kanikilu on 2009-03-11
How are you trying to edit it? Go to a terminal (Applications > Accessories > Terminal) and use ```
sudo nano /etc/apt/sources.list
``` to use the nano text editor. Otherwise press ALT+F2 and type ```
gksudo gedit /etc/apt/sources.list
``` for a GUI text editor.

---

### Post by kanikilu on 2009-03-11
> **yther said:**
> *Edit:  There sure have been a lot of people posting lately with mysteriously broken sources files... I wonder what is causing this... :?* Yeah, really. What's up with that :confused: Full moon, perhaps? :P

---

### Post by Henery on 2009-03-11
Wow you guy's are great thank you for your help update manager works again!
I hope I can help out around here in the future as I learn more about this kickass os!
Thank you guys!

---

### Post by ckmcm04 on 2011-04-11
Hi everyone, I have a similar problem as discussed and would like some help as I have not been able to get any updates. Thanks!

This is what I see in the terminal:


```
  GNU nano 2.2.2                File: /etc/apt/sources.list                                        


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/lucis](http://archive.canonical.com/lucis) partner
```

---

### Post by CharlesA on 2011-04-11
The error is in the last line, remove it and run this:

```
sudo apt-get update
```

---

### Post by 3rdalbum on 2011-04-11
And in future, don't manually edit your sources.list file. Use the Repositories window of Synaptic Package Manager instead, it's much safer. Also note that you already have the Lucid Partner repository added, and you've attempted to add it a second time.

---

### Post by ckmcm04 on 2011-04-11
thanks! it works and could finally get updates!

---

### Post by bodhi.zazen on 2011-04-11
> **3rdalbum said:**
> And in future, don't manually edit your sources.list file. Use the Repositories window of Synaptic Package Manager instead, it's much safer. Also note that you already have the Lucid Partner repository added, and you've attempted to add it a second time.

guilty as charged, I simply edit the sources.list by hand.

And, unless you are going to compile from source, I typically comment out the deb-src repos.

---

