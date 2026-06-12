---
title: "Kubuntu woes"
date: 2006-07-01
forum: Desktop Environments
---

### Post by tartarian on 2006-07-01
Is there any way to install firefox on Kubuntu? I've been into add/remove programs and run a search for firefox on all platforms and it gives me an entry but its greyed out and I can't select it. There's no package in adept and I downloaded the firefox.tar.bz but there's no configure script and no install file. 

Also, is there any way to change the file manager (adept) to either synaptic or something better, because I came from ubuntu and synaptic was better.

Finally, can anyone suggest anywhere where (and how) I can get a new log-in screen (username, password) and a new log-out screen. I had a look on kde-look.org but couldn't see anything (but my eye's aren't that good) :p 

Thanks for reading!
Any help would be just ace!

---

### Post by afffffff on 2006-07-01
for firefox type in konsole:
sudo apt-get install mozilla-firefox

---

### Post by AirRaven on 2006-07-01
Also, you can just get Synaptic by installing it from within Adept.

---

### Post by scxtt on 2006-07-01
if you download firefox from mozilla.com, you don't have to install it - you can run it from whereever you unpack the archive ...

---

### Post by Jucato on 2006-07-01
Let's take your issues one by one:

1. I can assure you that Firefox is there in the repositories. The package name is *firefox*, not mozilla-firefox (at least, for Dapper. Breezy still uses the mozilla-firefox name). I'm not sure why it's not showing up in Adept. I'm guessing that the problem probably lies in your /etc/apt/sources.list file. If you could post the contents of that file, we may take a look. Or you could also try installing firefox through the command line (it will give more descriptive error messages)
```
sudo aptitude update
sudo aptitude install firefox
```
See what those commands cough up.

2. The Adept package manager (not file manager, that's Konqueror) can be replaced by anything, like Synaptic or KPackage. All you need is to download those programs. Take note, though, that the Update Notifier only works with Adept. But you can still do things manually through Synaptic, if you're more comfortable using it.

3. Log-out screens can't be themed. You can only change the picture of Konqui snoozing. For login screens, you call that KDM themes. You first have to install the *kdmtheme* package, a KControl/System Settings module that allows you to install new KDM themes. Once that's installed, go to kde-look and download whatever KDM theme you like. Put it somewhere in your /home folder. Open up System Settings and KDM Theme Manager. Enter Administrator Mode. Click on Install New Theme and look for the .tar.gz theme you just downloaded. Once it's installed, click on the theme and hit Apply. 

Hope that helps

---

### Post by tartarian on 2006-07-02
Well, this is my /etc/apt/sources.list:
```


# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

this it the output of the terminal with both firefox and mozilla-firefox:
```


Password:
Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate
oliver@olivers-kubuntu:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnss3
E: Package firefox has no installation candidate
oliver@olivers-kubuntu:~$
oliver@olivers-kubuntu:~$
oliver@olivers-kubuntu:~$ sudo aptitude install firefox
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for firefox
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
oliver@olivers-kubuntu:~$

``` 
so I presume it's my sources. Any ideas on what I need to add?? Thanks!!

EDIT: Synaptic doesn't show up in adpet and neither does kdmtheme. I guess i have some sources missing??? :p

---

### Post by Jucato on 2006-07-02
All your repositories are disabled, that's why you can't install anything at all. 
Enable/Uncomment (remove the '#') the following lines. (You need root access of course).

> 
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


NOTE: I didn't ask you to enable/uncomment the deb-src. Usually, they're not used, unless you need to download/compile source code. Leaving them disabled usually speeds up the update process.

Then
```
sudo aptitude update
sudo aptitude install firefox
```

NOTE (again): I recommend using aptitude, because it handles metapackages and dependencies better than plain apt-get. To read about the difference, read this: [http://www.psychocats.net/ubuntu/aptitude.php](http://www.psychocats.net/ubuntu/aptitude.php)

Hope that helps

---

### Post by tartarian on 2006-07-02
Ok this is my sources list now :

```


# Line commented out by installer because it failed to verify:
deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted 
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
# Line commented out by installer because it failed to verify:
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main 
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu dapper-security main 
deb http://security.ubuntu.com/ubuntu dapper-security universe 
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe 

```

but it still doesn't find or install firefox or synaptic. Am I missing a repository???
Thanks for the help!

---

### Post by Jucato on 2006-07-02
I think there's something wrong with the [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) repositories.
Try replacing those with [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) or just plain [http://archive.ubuntu.com](http://archive.ubuntu.com)

---

