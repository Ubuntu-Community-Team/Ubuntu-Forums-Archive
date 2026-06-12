---
title: "Installing emeral-themes"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by zeroooooooooooo on 2008-02-09
I recently upgrades to Gusty, and got rid of all sorts of programs, including Beryl, which ran Emerald as a window decorator.  I have added the custom settings manager for Compiz-fusion under Gutsy, and am trying to manage themes(also with under Emerald), which I uninstalled and reinstalled as it was having issues crashing.

When I go into the theme chooser, nothing is in the list.  Also, getting GPLed and non-GLPed themes through that interface does nothing.

I have done

```
sudo apt-get update
sudo apt-get install emerald-themes
```

and it gives me the error:

Package emerald-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emerald-themes has no installation candidate

I think I have to add something to my sources.lst or something, but it has been a while since I have used Ubuntu at all, and I am a bit rusty.

Any help will be appreciated.

---

### Post by jan quark on 2008-02-09
to view your sources.list file run this in terminal
```

cat /etc/apt/sources.list
```

post the result please

thank you

---

### Post by zeroooooooooooo on 2008-02-09
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## Automatix repo
# deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END

# deb http://ubuntu.beryl-project.org/ feisty main
```
Thanks.

---

### Post by Tenken on 2008-02-09
Gutsy doesn't have a emerald theme package like Feisty that I know of. You can try [gnome-look ]("http://gnome-look.org")or [compiz-themes]("http://compiz-themes.org") for some themes. And to fetch themes from within the emerald manager you need to have subversion installed.

```
sudo apt-get install subversion
```

---

### Post by santiagoward2000 on 2008-02-09
> **Tenken said:**
> Gutsy doesn't have a emerald theme package like Feisty that I know of. You can try [gnome-look ]("http://gnome-look.org")or [compiz-themes]("http://compiz-themes.org") for some themes. And to fetch themes from within the emerald manager you need to have subversion installed.

```
sudo apt-get install subversion
```

That's true! There is no **emerald-theme** package on Gusty.

---

