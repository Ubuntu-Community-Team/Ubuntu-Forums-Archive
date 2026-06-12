---
title: "Update manager"
date: 2005-10-14
forum: Desktop Environments
---

### Post by waldorf on 2005-10-14
Under the update manager > preferences what should the software sources be?

The repositories got changed because I installed Adobe Reader and Jpilot and some others.

Thanks.

---

### Post by Dr. Nick on 2005-10-14
If you are in the United States use this in the file /etc/apt/sources.list.
open that as sudo in gedit and copy/paste. Your repos shouldnt mess up with installation of software though so Im not sure of your exact problem, Any error messages?

```
deb http://us.archive.ubuntu.com/ubuntu/ breezy main restricted multiverse universe   
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy main restricted   multiverse universe   

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted multiverse universe   
deb-src http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted  multiverse universe   

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ breezy universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ breezy universe 

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted multiverse universe  
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted   multiverse universe   

# deb http://security.ubuntu.com/ubuntu/ breezy-security universe 
# deb-src http://security.ubuntu.com/ubuntu/ breezy-security universe 

```

---

### Post by waldorf on 2005-10-14
I haven't had any problems I'm just seeing that folks are having troubles with updates and upgrades and so forth and I want to make sure that the update manager is looking to the right places and I'm not setting myself up for problems down the road.

I installed 5.10 RC1 and have been updating whenever it tells me to.

Thanks

---

### Post by Dr. Nick on 2005-10-14
Oh ok, 
The update manager should be pretty safe now since breezy is final but their is always the chance for error I guess, I was having a bit of trouble earler getting updates but figure it may just be a bit of congestion as I tried back after awhile and it went off flawlessly.

Welcome to the Forums

---

### Post by waldorf on 2005-10-14
Thanks again .

/etc/apt/sources.list

currently looks like this

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051005)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe



So is this okay?

---

### Post by Dr. Nick on 2005-10-14
Looks good to me, I wouldnt worry to much as long as it seems to be working, If you misconfigure something hitting "update" in synaptic will throw out a error window usually. The update manager also sems good at alerting you to errors or misconfigurations

---

### Post by waldorf on 2005-10-14
Well a final thank you for taking the time to calm my concerns.

Best to you

---

### Post by Dr. Nick on 2005-10-14
No problem , Just post if anything bad happens :)

---

### Post by iimess on 2005-10-14
I have a related issue:

Synaptic won't open. It will prompt for password but no window shows up.
ps -A|grep synaptic shows nothing

---

### Post by Dr. Nick on 2005-10-14
ps -A|grep synaptic shows nothing here but synaptic works. open a terminal and type sudo synaptic and look for error messages and post back

---

### Post by iimess on 2005-10-14
[QUOTE=Dr. Nick]ps -A|grep synaptic shows nothing here but synaptic works. open a terminal and type sudo synaptic and look for error messages and post back[/QUOTE]

Segmentation fault. Nothing more...

The last time I opened Synaptic was changing all hoary to breezy in repository and did reload/mark all several times.
(Eventually I cancelled the interface and upgraded with apt-get distro-upgrade. Synaptic exited normally)

apt-get update/install/etc works fine

---

### Post by Dr. Nick on 2005-10-14
Not sure why it segfaults, have you removed and reinstalled it using apt-get from the terminal

```
sudo apt-get remove synaptic
sudo apt-get install synaptic
```

If you do this though youll lose the update manager and a few other packages until you reinstall them. Not sure howto troubleshoot seg faults or if its possible, maybe someone else will be of help if remove/reeinstall synaptc doesnt work.

---

### Post by iimess on 2005-10-14
tried remove/install but no luck...

---

### Post by Dr. Nick on 2005-10-14
Dont know what to do then, if it doesnt get fixed in an update or with a reboot you may post back here  a new thread with a title more specific to your problem, it may get more peoples attention to your problem than this thread does

---

