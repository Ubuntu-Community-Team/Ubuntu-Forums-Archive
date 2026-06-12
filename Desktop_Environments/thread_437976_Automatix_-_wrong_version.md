---
title: "Automatix - wrong version"
date: 2007-05-09
forum: Desktop Environments
---

### Post by koz-man on 2007-05-09
I am a brand new Ubuntu user.  Today is my second day using the system.  Please forgive me if question is silly.

Today when I logged onto the computer, an icon appeared that said "updates available"  so i downloaded the one update.  It was for the program Automatix.

After the update was installed I could now longer use the Automatix program, saying that this version of Automatix is for Ubunto 6.01 something.  I am using Ubunto 7 something.

Yesterday the Automatix program worked just fine.  Anyway I need assistance in getting back the other version of Automatix.

Thanks in advance.

---

### Post by taurus on 2007-05-09
Post your /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```
And any reason you want to use automatix since everything is available for your in Applications -> Add/Remove.

---

### Post by koz-man on 2007-05-09
THANKS FOR REPLY:  BELOW IS WHAT I BELIEVE YOU REQUESTED.  Answer to question.  I don't know, It was preinstalled w/ the version of Ubuntu that I downloaded.  I guess I can just uninstall it .  Again im new and didn't know it was not standard.

jason@jason-laptop:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

#Automatix
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#Ichthux
deb [http://archive.ichthux.com/ichthux](http://archive.ichthux.com/ichthux) grace main
deb-src [http://archive.ichthux.com/ichthux](http://archive.ichthux.com/ichthux) grace main

#Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by taurus on 2007-05-09
> **koz-man said:**
> THANKS FOR REPLY:  BELOW IS WHAT I BELIEVE YOU REQUESTED.  Answer to question.  I don't know, It was preinstalled w/ the version of Ubuntu that I downloaded.  I guess I can just uninstall it .  Again im new and didn't know it was not standard.

jason@jason-laptop:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

[COLOR="Red"]#Automatix
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main[/COLOR]

#Ichthux
deb [http://archive.ichthux.com/ichthux](http://archive.ichthux.com/ichthux) grace main
deb-src [http://archive.ichthux.com/ichthux](http://archive.ichthux.com/ichthux) grace main

#Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

[COLOR="Red"]#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
[/COLOR]

Sorry but I don't think it comes with automatix already installed on your Feisty.  It is a 3rd party repo so you have to add it in by yourself after you installed Feisty.  Therefore, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove all the lines in red.  Save the changes and run

```
sudo aptitude --purge remove automatix2
sudo aptitude update
sudo aptitude upgrade
```
And if you insist on using automatix, please look at the link in my sig regarding 3rd party repos.

---

### Post by koz-man on 2007-05-09
okay i ran the following:

*gksudo gedit /etc/apt/sources.list*

there were no red lines.  any other ideas?  I did go to the Add/Remove Applications Manager but was not able to locate the Automatix program anywhere in there.  I checked in the "installed" and the "all open source" applications.


I am definitely trying to remove the automatix program.

---

### Post by rich.bradshaw on 2007-05-09
They won't be in red in the file, he means the ones he highlighted in red for you...

---

### Post by taurus on 2007-05-09
I _added_ the red color to those lines in your original /etc/apt/sources.list.

So, remove these lines then.

```

#Automatix
deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://www.getautomatix.com/apt edgy main
deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb http://www.getautomatix.com/apt edgy main

```
Save it.  Then run these commands from a terminal.

```
sudo aptitude --purge remove automatix2
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by koz-man on 2007-05-09
okay thanks I see now, ill do that

---

### Post by loserboy on 2007-05-09
or if you luv automatix like me then just hop over to [www.getautomatix.com](www.getautomatix.com) and ask arnie he'll have the fix right away

---

### Post by koz-man on 2007-05-09
thanks for my first lesson in using the Terminal.  Automatix has been removed.  I appreciate your patience.

---

