---
title: "Skype + KDE4.1 ... WTF??"
date: 2008-07-18
forum: Desktop Environments
---

### Post by SLA_leandrin on 2008-07-18
Hi.

What I will ask probably have a simple solution, but I really don't know how, so I'll ask you guys.

I installed  KDE4.1 my Ubuntu Hardy, just to test it. I did not liked it and then I've uninstalled.

I've installed adding this line to the repos;

```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
```
and running
```

sudo apt-get update & & sudo aptitude install kubuntu-desktop kde4-kdeplasmoids
```

Then, uninstalled by doing:
 ```
sudo apt-get remove - purge ubuntu-kde4-desktop kdeplasmoids
```

The problem is that during the installation of KDE4.1 it installs a bunch of other packages. The list is endless. 

```
sudo apt-get remove - purge ubuntu-*
sudo apt-get remove - purge kde *
sudo apt-get remove - purge kdeplasmoids-libs4
sudo aptitude AutoRemover - purge
```

The subjet is that Skype is using (I Think) qt, and it totally changed the look & feel, I do not like anything. In addition, it has [THIS]("http://ubuntuforums.org/showthread.php?t=795676") problem as well.

I tried to reinstall Skype, before deleting my folder /home /.skype, but remains the same. Please, someone who can help me to leave as it was originally skype!

Thanks...

---

### Post by SLA_leandrin on 2008-07-18
OK It's done...

All I've done is;

```
sudo apt-get remove libqt*
```

and reinstalled Skype.

---

