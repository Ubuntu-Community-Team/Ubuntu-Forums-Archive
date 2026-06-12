---
title: "Can't Install Dolphin on GNOME Ubuntu 10.10"
date: 2010-11-12
forum: Desktop Environments
---

### Post by 31632531 on 2010-11-12
I've been trying to install Dolphin File Manager in GNOME Ubuntu 10.10

This is the output I'm getting when I try to install..

```
$ pkginst dolphin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 dolphin : Depends: kdebase-runtime but it is not going to be installed
           Depends: libkdeui5 (>= 4:4.5) but it is not going to be installed
           Depends: libkfile4 (>= 4:4.5.1) but it is not going to be installed
           Depends: libkio5 (>= 4:4.5.1) but it is not going to be installed
           Depends: libknewstuff3-4 (>= 4:4.5) but it is not going to be installed
           Depends: libkonq5 (>= 4:4.4.1) but it is not going to be installed
           Depends: libkparts4 (>= 4:4.5) but it is not going to be installed
           Depends: libkutils4 (>= 4:4.4.90) but it is not going to be installed
           Depends: libnepomuk4 (>= 4:4.5) but it is not going to be installed
           Depends: libnepomukquery4a (>= 4:4.5) but it is not going to be installed
           Recommends: kfind but it is not going to be installed
E: Broken packages

```Any thoughts?

---

### Post by hellnest on 2010-11-12
> **31632531 said:**
> I've been trying to install Dolphin File Manager in GNOME Ubuntu 10.10

This is the output I'm getting when I try to install..

```
$ pkginst dolphin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 dolphin : Depends: kdebase-runtime but it is not going to be installed
           Depends: libkdeui5 (>= 4:4.5) but it is not going to be installed
           Depends: libkfile4 (>= 4:4.5.1) but it is not going to be installed
           Depends: libkio5 (>= 4:4.5.1) but it is not going to be installed
           Depends: libknewstuff3-4 (>= 4:4.5) but it is not going to be installed
           Depends: libkonq5 (>= 4:4.4.1) but it is not going to be installed
           Depends: libkparts4 (>= 4:4.5) but it is not going to be installed
           Depends: libkutils4 (>= 4:4.4.90) but it is not going to be installed
           Depends: libnepomuk4 (>= 4:4.5) but it is not going to be installed
           Depends: libnepomukquery4a (>= 4:4.5) but it is not going to be installed
           Recommends: kfind but it is not going to be installed
E: Broken packages

```Any thoughts?

First, dolphin is a file manager for KDE Desktop not Gnome Desktop. So absolutely you will found a lot of unsatisfied dependencies... :) You got nautilus already for a file manager in Gnome,...

---

### Post by 31632531 on 2010-11-12
I know that it is a file manager for KDE.  Nautilus doesn't support column view (OSX style). I like GNOME; I have just got comfortable using column view at work.  I like the work flow.

I suppose I should have asked; is there anyway to let apt satisfy the dependencies without having to manually follow the path of errors??

(I tried installing all the packages prescribed by apt when trying to install dolphin and got this result);

```
$ pkginst kdebase-runtime libkdeui5 libkfile4 libkio5 libknewstuff3-4 libkonq5 libkparts4 libkutils4 libnepomuk4 libnepomukquery4a kfind dolphin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 kdebase-runtime : Depends: libkdnssd4 (>= 4:4.5) but it is not going to be installed
                   Depends: libkhtml5 (>= 4:4.5) but it is not going to be installed
                   Depends: libkmediaplayer4 (>= 4:4.5) but it is not going to be installed
                   Depends: libknotifyconfig4 (>= 4:4.5) but it is not going to be installed
                   Depends: libplasma3 (>= 4:4.5.1) but it is not going to be installed
                   Depends: libqt4-svg (>= 4:4.5.3) but it is not going to be installed
                   Depends: kdelibs5-plugins (>= 4:4.5.1) but it is not going to be installed
                   Depends: plasma-scriptengine-javascript (= 4:4.5.1-0ubuntu3.1) but it is not going to be installed
                   Recommends: kubuntu-debug-installer but it is not going to be installed
 libkdeui5 : Depends: libqt4-svg (>= 4:4.7.0~beta2) but it is not going to be installed
 libkfile4 : Depends: libqt4-svg (>= 4:4.7.0~beta2) but it is not going to be installed
 libkio5 : Depends: libqt4-svg (>= 4:4.7.0~beta2) but it is not going to be installed
           Recommends: kdelibs5-plugins (= 4:4.5.1-0ubuntu8) but it is not going to be installed
 libknewstuff3-4 : Depends: libqt4-svg (>= 4:4.7.0~beta2) but it is not going to be installed
 libkparts4 : Depends: libqt4-svg (>= 4:4.7.0~beta2) but it is not going to be installed
 libkutils4 : Depends: libqt4-svg (>= 4:4.7.0~beta2) but it is not going to be installed
 libnepomuk4 : Depends: libqt4-svg (>= 4:4.7.0~beta2) but it is not going to be installed
 libnepomukquery4a : Depends: libqt4-svg (>= 4:4.7.0~beta2) but it is not going to be installed
E: Broken packages

```

Is this going to go on like this for a while or is there any way to mitigate the whole thing?

---

### Post by sidzen on 2010-11-13
> **31632531 said:**
> I know that it is a file manager for KDE. . . .
Is this going to go on like this for a while or is there any way to mitigate the whole thing?

Have you tried, at the terminal,
[PHP]sudo apt-get build-dep dolphin && sudo apt-get -f install dolphin[/PHP] ?

If this doesn't work, it could very well be an unpractical (impractical?) thing to attempt.

Best wishes!

---

### Post by 31632531 on 2010-11-13
> **sidzen said:**
> Have you tried, at the terminal,
[PHP]sudo apt-get build-dep dolphin && sudo apt-get -f install dolphin[/PHP] ?

If this doesn't work, it could very well be an unpractical (impractical?) thing to attempt.

Best wishes!

Yes I've tried this, I have a feeling you are right about the practicality.  Too bad.

Thanks for the help!

---

