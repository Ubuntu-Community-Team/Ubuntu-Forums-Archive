---
title: "Can't Open Synaptic Package Manager"
date: 2009-04-26
forum: General Help
---

### Post by papasmurf6768 on 2009-04-26
Hi Guys,

F.Y.I. This is my first thread so I'm not really sure what I'm doing.  Also, I'm very new to Ubuntu so please keep it to beginner talk.  Thanks.

Ok heres my problem.  When I go to open the package manager, I get an error:  

                                 E: Type '”deb” is not known on line 58 in source list /etc/apt/sources.list
 E: The list of sources could not be read.
 Go to the repository dialog to correct the problem.
 E:_cache->open()failed, please report.
 
I'm really hoping this is an easy fix.  Thanks everyone

-Papasmurf6768

---

### Post by danwood76 on 2009-04-26
Im assuming you've added a line to your sources.list file manually and not through synaptic.

can you post the output of this from the gnome terminal:
```

cat /etc/apt/sources.list

```

---

### Post by papasmurf6768 on 2009-04-26
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports restricted main multiverse universe
“deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
“deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
“deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”

I ran that code and here's what I got.  Thanks for replying so fast. :KS

---

### Post by nothingspecial on 2009-04-26
> **papasmurf6768 said:**
> 

“deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
“deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”
“deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main”

I ran that code and here's what I got.  Thanks for replying so fast. :KS

You`ve got speech marks around the awn lines plus you`ve duplicated the first line. Also they are for hardy.

---

### Post by nothingspecial on 2009-04-26
Sorry, I suppose I should have explained how to fix it.

```
gksudo gedit /etc/apt/sources.list
```

Remove those 3 lines and replace them with

```
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main
```

Do not change anything else. Save the file
Then ```
sudo apt-get update
```

and you should be good to go.

---

### Post by papasmurf6768 on 2009-04-26
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: You may want to run apt-get update to correct these problems

I did exactly what you said, and in the terminal, at the end of all the other stuff, it said this.  Does this mean anything?  Or is my problem fixed?

---

### Post by nothingspecial on 2009-04-26
You need to add the key. See [[COLOR="Red"]here[/COLOR]]("https://launchpad.net/~awn-testing/+archive/ppa")

---

### Post by papasmurf6768 on 2009-04-26
I dont't get it...

---

### Post by papasmurf6768 on 2009-04-26
I don't get it...typo.  But yah I'm looking all over for trying to figure out how to add this key but I can't find anything.  Anyone know anyone beginner-links?

---

### Post by Praxicoide on 2009-04-26
Type the following in the terminal

```
gpg --keyserver keyserver.ubuntu.com --recv 7D2C7A23BF810CD5 && gpg --export -a 7D2C7A23BF810CD5 | sudo apt-key add -
```

This should install the necessary key for that ppa.

---

### Post by nothingspecial on 2009-04-26
On a side note, why do you want the testing version? 
Why not install the stable version in the repos.

---

