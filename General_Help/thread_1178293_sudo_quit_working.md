---
title: "sudo quit working"
date: 2009-06-04
forum: General Help
---

### Post by bolweval on 2009-06-04
Anytime i attempt to use the sudo command i get this message

E:Type 'sudo' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.

I've searched around the forums but hard to sift through the search results for this long error message, any help would be greatly appreciated, thank you.

---

### Post by drs305 on 2009-06-04
When you say "anytime", do you really mean when you try to run "apt-get" or "aptitude" or another package manager, or does it happen even if you run a command such as "sudo ls"?

Well, let's start by looking at the message:
```

cat /etc/apt/sources.list

```

Even better would be the following assuming package management is what you are really having problems with:
```

gksudo gedit +56 /etc/apt/sources.list 

```


Line 56 shouldn't be in your sources.list. Delete it, place a comment symbol # at the start of the line, or post the contents here if you don't understand ...

---

### Post by bolweval on 2009-06-04
thanks for responding

This is what I get from " ls"

compiz-check  examples.desktop         google-earth  Public     Videos
Desktop       Firefox_wallpaper.png  Music       steam ubuntu
Documents     googleearth         Pictures       Templates


This is what I get from "cat /etc/apt/sources.list"

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
sudo apt-get update


sudo apt-get update


And this is what I get from "
gksudo gedit #56 /etc/apt/sources.list        

opens an unsaved document 1 - gedit

---

### Post by drs305 on 2009-06-04
You have an extra line in your sources.list. 

Open the file for editing:
```

gksudo gedit /etc/apt/sources.list

```

Remove the last line (this one):
> [COLOR="DarkRed"]sudo apt-get update[/COLOR]

Save the file and update your sources.list:
```

sudo apt-get update && sudo apt-get upgrade

```

Note: typo in my initial post: to open at a specific line with gedit, +LINENUMBER.

---

### Post by bolweval on 2009-06-04
OK, removed the extra line "sudo apt-get update" now it only says that once, and tried to update and still get this message "E: Type 'sudo' is not known on line 56 in source list /etc/apt/sources.list" Should I remove the other "sudo apt-get update" at the end of the list?

Thanks for the help


> **drs305 said:**
> You have an extra line in your sources.list. 

Open the file for editing:
```

gksudo gedit /etc/apt/sources.list

```Remove the last line (this one):


Save the file and update your sources.list:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by iponeverything on 2009-06-04
> Should I remove the other "sudo apt-get update" at the end of the list?

:) yes

---

### Post by Chronon on 2009-06-04
"sudo apt-get update" does not specify the location of a repository.  ;)

---

### Post by drs305 on 2009-06-04
Edit: Too late.

Yes, I didn't understand that the second one was part of the sources.list as well. You should be good after the removal. Every line in sources.list should begin with "deb" or a # symbol.

---

### Post by bolweval on 2009-06-04
Awesome!

Fixed guys/gals 

This place has made my transition from Windows to Linux fairly painless, I love this OS.

Thanks

---

