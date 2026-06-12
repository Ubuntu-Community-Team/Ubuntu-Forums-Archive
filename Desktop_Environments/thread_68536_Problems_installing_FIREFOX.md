---
title: "Problems installing FIREFOX"
date: 2005-09-23
forum: Desktop Environments
---

### Post by narmenia on 2005-09-23
im really new to linux and a complete n00b.
im using KUBUNTU.

i really need help installing firefox on KUBUNTU.

i tried installing it on Knaptic > world wide web > mozilla-firefox-locale-en-gb
uninstalled it and reinstalled but still no firefox on the internet tab

on the Konsole:
ws02@ws02:~$ sudo apt-get update
Reading package lists... Done
ws02@ws02:~$ sudo apt-get install mozilla-firefox
Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate

waaaaaaaaaaaaaa... im going crazy... T_T. i have been searching the forums and googling for more than 24 hours but still no firefox... ](*,) 

need help... thanx

*edit: i've tried ubuntu and it has firefox... can i change Ubuntu's GNOME to KDE and still retain FIREFOX,GAIM,ect.???

---

### Post by Knome_fan on 2005-09-23
mozilla-firefox-locale-en-gb are just the translations, so only installing them will not give you firefox.

What's strange is that mozilla-firefox is not available, as it should be and normally is available.

Did you somehow change your sources.list?
Could you post your /etc/apt/sources.list so people can take a look and see if something is wrong?

---

### Post by narmenia on 2005-09-23
```
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
```

is this the one??? > media:/hda1/etc/apt/sources.list
thanx in advance for the help...

---

### Post by Knome_fan on 2005-09-23
Ah, I think I know what the problem is.

You've only got the kubuntu cdrom as a repository, all the others are commented out (that is, there's a # in front of them)

Simply removing the # in front of the lines starting with deb, or deb-src (Note, you'll have to be root to be allowed to edit this file) should fix your problem.

After you did this, run sudo apt-get update and then install mozilla-firefox.

Have fun!

---

### Post by narmenia on 2005-09-23
i may have done something wrong...

at 1st a could not edit the sources.list...

now using the Konsole:
at 1st it opened but only a blank document...
now i typed:
```
ws02@ws02:~$ sudo kate /ect/apt/sources.list
kate: ERROR: Communication problem with kate, it probably crashed.
ws02@ws02:~$ sudo kwrite /ect/apt/sources.list
Qt: Locales not supported on X server
Error: "/var/tmp/kdecache-ws02" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-ws02" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
```

OMG!!! im going NUTZ... T_T ](*,)

---

### Post by Knome_fan on 2005-09-23
Ok, first, could you reboot, this should get rid of temp files with wrong permissions, I hope.

Second, could you try to open the document with:
kdesu kwrite /etc/apt/sources.list

Hope this helps.

---

### Post by Gezzer on 2005-09-23
kdesu kate
in a konsole

browse to the etc/apt/sources-list file
open in kate then edit

save changes
in the same konsole
su apt-get update

then open kynaptic/synaptic to do the install ...

---

### Post by narmenia on 2005-09-23
a window pops up every reboot and asks for the password. it opens kate but just dissapears... i restarted the computer twice... but only a SHUTDOWN of the PC for a few seconds removed the crash... hehehe

now i've done it... weeeeeeeeeeee...

is this correct?
```
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb http://ph.archive.ubuntu.com/ubuntu hoary main restricted
 deb-src http://ph.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://ph.archive.ubuntu.com/ubuntu hoary-updates main restricted
 deb-src http://ph.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://ph.archive.ubuntu.com/ubuntu hoary universe
 deb-src http://ph.archive.ubuntu.com/ubuntu hoary universe

 deb http://security.ubuntu.com/ubuntu hoary-security main restricted
 deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

 deb http://security.ubuntu.com/ubuntu hoary-security universe
 deb-src http://security.ubuntu.com/ubuntu hoary-security universe
``` 

when i do "sudo apt-get update" i now connects but...

```
ws02@ws02:~$ sudo apt-get update
Err http://ph.archive.ubuntu.com hoary Release.gpg
  Could not connect to ph.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ph.archive.ubuntu.com hoary-updates Release.gpg
  Could not connect to ph.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Ign http://security.ubuntu.com hoary-security Release
Ign http://ph.archive.ubuntu.com hoary Release
Ign http://security.ubuntu.com hoary-security/main Packages
``` 

how long does an update take? im on 384kbps (around 40KB/s)

btw thanx a lot guyz... /no1

---

### Post by Knome_fan on 2005-09-23
Yes, that's correct.

Now I'm only wondering why you are getting errors when updateing?
I just checked an the mirror seems to be online.

Could you try it again and see if it was just a temporary problem?
Also, did you succeed in install firefox yet?

---

### Post by narmenia on 2005-09-23
```
ws02@ws02:~$ sudo apt-get update
Password:
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 [COLOR=RED](1.0.0.0)[/COLOR], connection timed out
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) hoary Release.gpg
  Could not connect to ph.archive.ubuntu.com:80 [COLOR=RED](1.0.0.0)[/COLOR], connection timed out
```

are those 1.0.0.0 ok? are they supposed to be IP address? :roll: 
btw im on a LAN with a router. do i have to forward some PORTS?

```
assword:
Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list http://ph.archive.ubuntu.com hoary/main Pac
kages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i
386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com hoary/restrict                ed Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_hoary_restric                ted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com hoary/universe                 Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_hoary_universe_                binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com hoary-updates/                main Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_hoary-updat                es_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ph.archive.ubuntu.com hoary-updates/                restricted Packages (/var/lib/apt/lists/ph.archive.ubuntu.com_ubuntu_dists_hoary                -updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/m                ain Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security                _main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/r                estricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-se                curity_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/u                niverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-secu                rity_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: [COLOR=RED]You may want to run apt-get update to correct these problems[/COLOR]
E: Package mozilla-firefox has no installation candidate
ws02@ws02:~$
```

---

### Post by Knome_fan on 2005-09-23
Hm, that's really strange.

I'm not entirely sure, but I think you normally shouldn't need to forward any ports if "normal" internet (that's http) works.

But are you using a proxy?
In this case this might help:
[http://ubuntuforums.org/showthread.php?t=67958&highlight=proxy](http://ubuntuforums.org/showthread.php?t=67958&highlight=proxy)

Another method is described here (post #4):
[http://www.ubuntuforums.org/showthread.php?t=63496&highlight=proxy+authentication](http://www.ubuntuforums.org/showthread.php?t=63496&highlight=proxy+authentication)

---

### Post by narmenia on 2005-09-23
im on NAT using DHCP... no proxy...

internet is fine... im using kubuntu to post this reply...

in the Konsole the bottom portion says:
```
29% [Connecting to ph.archive.ubuntu.com (1.0.0.0) [Connecting to security .ubu
```
the % increases overtime but will never goes up to 100%... 
i really have no idea if its just connecting or already downloading the updates... ](*,)

***EDIT: FIXED!!! [http://ubuntuforums.org/showthread.php?t=68683](http://ubuntuforums.org/showthread.php?t=68683)
TYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTYTY  :grin:

---

