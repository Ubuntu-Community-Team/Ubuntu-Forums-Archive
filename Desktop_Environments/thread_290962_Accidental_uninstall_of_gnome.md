---
title: "Accidental uninstall of gnome"
date: 2006-11-01
forum: Desktop Environments
---

### Post by hereford2004 on 2006-11-01
When using Symantec, I foolishly (but accidentally) uninstalled the following packages:

gnome-power-manager
gnome-session
notification-daemon
ubuntu-desktop
update-notifier

Since GNOME won't come up now (and I hadn't installed any other desktop packages), I have tried (unsuccessfully) to add my Ubuntu 6.06 livecd to sources.list and use aptitude to reinstall the packages. Apt-get won't recognize the cdrom when I use the

>apt-cdrom
>aptitude update
>aptitude install gnome-power-manager

commands to try to install the packages; it responds with an error stating that the package couldn't be found in any of the repositories. Installing from the internet repositories (at least I think) won't work because I can't get to the point where I can log in. 

Any suggestions on other ways to get these packages reinstalled, or obvious reasons why what I did might have failed?

---

### Post by taurus on 2006-11-01
Try

```
apt-cdrom add
aptitude update
aptitude install gnome-power-manager
```

---

### Post by hereford2004 on 2006-11-01
Whoops.. that was what I meant to write.
I meant to say, 

>apt-cdrom add
>aptitude update
>aptitude install gnome-power-manager

---

### Post by taurus on 2006-11-01
Are you in the recovery mode right now?  What does your /etc/apt/sources.list look like anyway?

You can always try

```
aptitude update
aptitude install ubuntu-desktop
```

---

### Post by Drezliok on 2006-11-01
sudo Apt-get install ubuntu-desktop


That should put everything back. I used it once.

[edit]
Someone beat me to it.
[edit]

---

### Post by hereford2004 on 2006-11-01
Tried that just now (had to reboot).

The message was, for both 'apt-get install ubuntu-desktop' and 'aptitude install ubuntu-desktop' after the 'apt-cdrom' and update commands:

>>>>>>
Reading package lists...   Done
Building dependency tree...Done

Package ubuntu-desktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.
E. Package ubuntu-destop has no installation candidate.
>>>>>>

---

### Post by gerowen on 2006-11-01
You still have network connectivity without Gnome started, or at least you should, just let it use the internet repos.

---

### Post by hereford2004 on 2006-11-01
Every time I update apt-get or aptitude, it states that it is failing to access the archive sites. Or did I misunderstand what you just posted..?

---

### Post by taurus on 2006-11-01
Why don't you post your /etc/apt/sources.list here to see what's wrong with it?

```
more /etc/apt/sources.list
```

---

### Post by hereford2004 on 2006-11-02
Here 'tis:

>>>>>>>>>>>>>>>>>>>>>
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531)]/ dapper main restricted
deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release amd64 (20060531)]/ dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025)]/ edgy main restricted

>>>>>>>>>>>>>>>>>>>>>>>>>>>

---

### Post by Psquared on 2006-11-26
I have got the same problem.

I have tried all the suggestions. The live CD (iso) is my only source for the packages, but in that format I don't think apt-get can reinstall the desktop. What I wonder is if there is a way to unpack the iso, put it in a directory and point sources.list to it. All my data is still there so I don't want to reformat.

Would the alternate CD work better? Is it still in ISO format?

One thing about Ubuntu is the Ubuntu-Desktop is integrated with so many packages. I was having trouble with dbus and thought if I uninstalled and reinstalled it the files would get back in their proper location. I forgot that by uninstalling the desktop that I would lose internet connectivity. So all I've got left is the Live CD.

---

