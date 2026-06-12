---
title: "[mini9] how to turn of wifi &amp; bluetooth after intrepid install?"
date: 2008-11-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by obitux on 2008-11-20
Hi!
I've a dell mini 9 with a fresh install of Intrepid.
(I didn't like dell default version).
It works great but I would like can turn off wifi and bluetooth in order to preserve battery.
I thought to install the plane mode utility existing on Dell Ubuntu, downloading the good package on
[http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/)
and forcing architecture, but I don't know the program name...
Can anyone help me?
Or if you know another way...
Thanks!
(and I apologize if my English isn't perfect ;) )

---

### Post by ytsejam1138 on 2008-11-20
```
sudo apt-get aircraft-manager
```

This will install an app located under Settings>Preferences called Airplane Mode (or something like that).  You can turn off Bluetooth and/or WiFi with this.

---

### Post by obitux on 2008-11-20
Hi!
Tanks for your help, I'm progressing.
I remember that I'm not runing a lpia kernel, and I don't use dell-mini repository.
So I've downloaded the deb at
[http://dell-mini.archive.canonical.com/dists/hardy-netbook-base/universe/binary-lpia/aircraft-manager_5_all.deb](http://dell-mini.archive.canonical.com/dists/hardy-netbook-base/universe/binary-lpia/aircraft-manager_5_all.deb)
The install run successfully. (with no architecture issue)
But now, when I try to launch aircraft-manager, I get this answer in the terminal :
```
Traceback (most recent call last):
  File "/usr/bin/aircraft-manager", line 312, in <module>
    app = GUI()
  File "/usr/bin/aircraft-manager", line 74, in __init__
    self.cbWIFI.set_active(self.getWifiState())
  File "/usr/bin/aircraft-manager", line 304, in getWifiState
    nmOutput = nm.getWirelessEnabled()
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Method "getWirelessEnabled" with signature "" on interface "(null)" doesn't exist

```

Can anybody help me?

*I imagine I'm not the first one who install a real ubuntu version on a dell mini 9 trying to manage wifi and bluetooth, am I wrong? It's strange...*

---

### Post by ytsejam1138 on 2008-11-20
Neither do I, I'm running 8.10 and I installed with no problems.  If you open Synaptic Package Manager and search for 'aircraft' you should see it.

---

### Post by macoman_86 on 2008-11-20
hello at all,i'm italian and please don't kill me for my english.........

i've a question about my dell mini....i've installed ubuntu 8.10 with usb pendrive and it's great but the bluetooth for the new ubuntu don't exist....
i tried a lot of command founded in forums but the bt is dead!	:(
in the defaut version it was all ok but in this i can't trigger the bt.....

thanks

---

### Post by armandh on 2008-11-20
did you get the blue tooth option? 
try a usb bluetooth

---

### Post by obitux on 2008-11-21
Please macoman_86, create your own thread, our issues are different.

ytsejam1138, it's strange, I haven't this package in my repositories.
What's yours sources.list?
Me :
```
## DEPOTS PRINCIPAUX
deb http://fr.archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse


## DEPOTS DE MISES A JOUR DE SECURITE
deb http://fr.archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse

## DEPOTS DE MISES A JOUR IMPORTANTES
deb http://fr.archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu intrepid-updates main restricted universe multiverse

###############################################################################

## DEPOTS DE MISES A JOUR EN PRES VERSION
deb http://fr.archive.ubuntu.com/ubuntu intrepid-proposed main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu intrepid-proposed main restricted universe multiverse

## DEPOTS NON PRIS EN CHARGE
deb http://fr.archive.ubuntu.com/ubuntu intrepid-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu intrepid-backports main restricted universe multiverse

###############################################################################
## DEPOTS TIERCES PARTIES

# DEPOTS COMMERCIAUX
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

# DEPOTS MEDIBUNTU
# Vous devez saisir le cles suivante :
# wget -q http://fr.packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

deb http://fr.packages.medibuntu.org/ intrepid free non-free
# deb-src http://fr.packages.medibuntu.org/ intrepid free non-free

# DEPOTS WINE
# Vous devez saisir la cles suivante :
# wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

deb http://wine.budgetdedicated.com/apt intrepid main
# deb-src http://wine.budgetdedicated.com/apt intrepid main

# THEMES
deb http://debian.vogelweith.com/ intrepid zgegthemes
# deb-src http://debian.vogelweith.com/ intrepid zgegthemes

# UBUNTU TWEAKS
deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/tualatrix/ubuntu intrepid main

# OOO3
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

## GOOGLE
deb http://dl.google.com/linux/deb/ stable non-free

## UNR
deb http://ppa.launchpad.net/netbook-remix-team/ubuntu intrepid main

```

```
sudo apt-cache search aicraft
```
is void

---

### Post by ytsejam1138 on 2008-11-21
Here is my sources.list

```
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```

---

### Post by obitux on 2008-11-23
Really, it's seems unbelievable but this package isn't in repositories for me...
Can anybody explain that?

---

### Post by ytsejam1138 on 2008-11-23
Here are some screens from my Software Sources.  Maybe these can help.

---

### Post by tscheckoff on 2008-11-24
Same problem here.

The package "aircraft-manager" doesn't seem to be in the repositories. (BTW: I'm using the german mirror)

I even copied ytsejam1138's sources.list and did an ```
sudo apt-get update
``` - no luck either.

Does anybody know where to get a working .deb for Intrepid?

---

### Post by ytsejam1138 on 2008-11-24
Here's the one from Hardy Heron.  Maybe this will work for you guys.

[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/source/aircraft-manager_belmont11.tar.gz](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/source/aircraft-manager_belmont11.tar.gz)

---

### Post by tscheckoff on 2008-11-24
Thanks for the link. 

Compiling went smoothly (as far as i can tell) but when I run aircraft-manager in a terminal I get this:

```
tscheckoff@mini:~/Desktop/aircraft-manager$ aircraft-manager
Traceback (most recent call last):
  File "/usr/local/bin/aircraft-manager", line 359, in <module>
    app = GUI()
  File "/usr/local/bin/aircraft-manager", line 79, in __init__
    self.cbBT.set_active(self.getBtState())
  File "/usr/local/bin/aircraft-manager", line 302, in getBtState
    f = open("/tmp/bt_status", "r")
IOError: [Errno 2] No such file or directory: '/tmp/bt_status'
```

Still no luck. 

Any hints?

---

### Post by ytsejam1138 on 2008-11-24
If you got it installed you should see Airplane Mode under Settings>Preference  What happens when you try to run it this way?

---

### Post by tscheckoff on 2008-11-24
Nothing. That's why I started it in a terminal window - to see if any error messages occur.

Seems the error is related to some bluetooth thingy (bt_status), but I'm no expert....

---

### Post by ytsejam1138 on 2008-11-24
Sounds like it wasn't compiled and installed correctly.  What happens if you run this in terminal:

sudo /usr/bin/aircraft-manager

---

### Post by tscheckoff on 2008-11-24
Exactly the same output when run as root. 

I'm giving up for now...

---

### Post by ytsejam1138 on 2008-11-24
Okay, now I'm in the same boat.  I had to do a reinstall of Ubuntu this evening due some hardware upgrades and I cannot seem to get aircraft-manager installed again.  I didn't do anything special the first time around it was just there when I went to install it.

---

### Post by obitux on 2008-11-25
Welcome to the club, ytsejam1138!

---

### Post by ytsejam1138 on 2008-11-25
[SOLUTION]
I finally figured this one out.

Download this aircraft-manager .deb [aircraft-manager](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/aircraft-manager_belmont11_all.deb)

Now in terminal navigate to the folder with the file and type:

```
sudo dpkg -i aircraft-manager_belmont11_all.deb
```

This will put an application in System>Preferences called Airplane Mode

---

### Post by tscheckoff on 2008-11-25
Cool. Works like a charm! \\:D/

Thx, you made my day!

---

### Post by obitux on 2008-11-25
Thanks!!!!

---

