---
title: "how the hell do i edit sources.list"
date: 2006-01-04
forum: General Help
---

### Post by sebweb on 2006-01-04
i cant do a god damn thing to it and thre is one line in it that need to be changed so i can use the synaptic package manager  and repositories

ps i am a nooby

---

### Post by gatorbrit on 2006-01-04
You have to have root access - type:
```
sudo gedit sources.list

```
Then enter your password at the prompt and you can make changes.

---

### Post by byen on 2006-01-04
actually it is
sudo gedit /etc/apt/sources.list

goodluck.

---

### Post by Omnios on 2006-01-04
This is the unofficial starter guide from the last release but its generaly similar and will give you an idea of what is going on.

 [http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")

 Now what you want to do is open the sources file as above with sudo gedit.

 There will be a few entries in there that are commented out # with copy and past  restricted and univers with out the #, this stops the entries from dissapearing if you uncheck the repositories in synaptic.

 Also read 

 [http://ubuntuforums.org/forumdisplay.php?f=41]("http://ubuntuforums.org/forumdisplay.php?f=41")
 
 Any other problems or uncertanties just ask.

---

### Post by Omnios on 2006-01-04
This is my sources.list if it helps any.

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


 deb http://ca.archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
 deb http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://ca.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://ca.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

 deb http://ca.archive.ubuntu.com/ubuntu breezy multiverse

deb http://wine.sourceforge.net/apt/ binary/

#deb http://wine.sourceforge.net/apt/ binary/
#deb-src http://wine.sourceforge.net/apt/ source/
```

---

### Post by FizDev on 2006-01-04
You can also use "nano" instead of gedit. It will open the text in the terminal instead of gedit in an x environnement. :)
sudo nano /etc/apt/sources.list

---

### Post by Omnios on 2006-01-04
Also after setting up your repo's use 

 ```
sudo apt-get update
```

 to update you repositories.

---

### Post by harisund on 2006-01-05
Can;t you add a repository using Synaptic itself?

---

### Post by Gray. on 2006-01-05
Yes you can. It's just faster this way.

---

