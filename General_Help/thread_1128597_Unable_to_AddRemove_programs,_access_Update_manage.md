---
title: "Unable to Add/Remove programs, access Update manager or Synaptic package Manager"
date: 2009-04-17
forum: General Help
---

### Post by krister bülü on 2009-04-17
Are there any errors apparent in my sources.list?

At the bottom it mentions WineHQ 8.10 Intrepid Ibex but I'm running Hardy Heron. 


# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta i386 (20080319)]/ hardy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy universe
eb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"

---

### Post by t-o-c on 2009-04-17
What is the error message you receive when accessing synaptic?

---

### Post by krister bülü on 2009-04-17
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I already ran sudo dpkg --configure -a

---

### Post by oldos2er on 2009-04-17
> **krister bülü said:**
> are there any errors apparent in my sources.list?

At the bottom it mentions winehq 8.10 intrepid ibex but i'm running hardy heron. 


# deb cdrom:[ubuntu 8.04.1 _hardy heron_ - release i386 (20080702.1)]/ hardy main restricted
# see [http://help.ubuntu.com/community/upgradenotes](http://help.ubuntu.com/community/upgradenotes) for how to upgrade to
# newer versions of the distribution.

[COLOR=blue]deb cdrom:[ubuntu 8.04 _hardy heron_ - beta i386 (20080319)]/ hardy main restricted[/COLOR]
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## major bug fix updates produced after the final release of the
## distribution.
Deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## n.b. Software from this repository is entirely unsupported by the ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe will not receive any review or updates from the ubuntu security
## team.
Deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## n.b. Software from this repository is entirely unsupported by the ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse will not receive any review or updates from the ubuntu
## security team.
Deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## uncomment the following two lines to add software from the 'backports'
## repository.
## n.b. Software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## also, please note that software in backports will not receive any review
## or updates from the ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## uncomment the following two lines to add software from canonical's
## 'partner' repository. This software is not part of ubuntu, but is
## offered by canonical and the respective vendors as a service to ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
[COLOR=blue]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy universe
eb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main[/COLOR]

[COLOR=blue]deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #winehq - ubuntu 8.10 "intrepid ibex[/COLOR]"

 You  should add a comment mark (#) to the front of each line I've marked in blue. Adding repos from different releases is never a good idea.

 To edit this file, run
```
gksu gedit /etc/apt/sources.list
``` Once you're finished, run
 ```
sudo apt-get update
```

---

### Post by Bobrm2 on 2009-09-13
I've done as suggested, above. Have no access to Synaptic, Add/Remove. In main menu (/system/admin/ I am unable to select "Software sources" and "Login Window". THe only thing allowed in either Alacarte or Main Menu (/system/main menu) is "File Browser". etc etc.  

Have sudo apt-get upgrade, sudo apt-get install. No joy

Can and have accessed Synaptic through sudo synaptic

Any help much appreciated.

---

### Post by Bobrm2 on 2009-09-13
Excuse me , Running JJ 9.04, and have an ATI card.

---

### Post by jmszr on 2009-09-13
Bobbrm2,

I had a similar problem, the fix was:```
sudo rm /var/cache/apt/*.bin
```

Perhaps that will help your problem.

---

### Post by Bobrm2 on 2009-09-13
> **jmszr said:**
> Bobbrm2,

I had a similar problem, the fix was:```
sudo rm /var/cache/apt/*.bin
```

Perhaps that will help your problem.

There was some improvement, Synaptic didn't gray out, but doesn't respond. Was able to select other options in /system/preferences, "Debian" etc, still no "add/remove" etc. will keep at it. I learning the commands as I go. Thanks for the quick reply.
Bob

---

### Post by Bobrm2 on 2009-09-13
Still haven't access to user and groups?

---

### Post by biebel on 2009-09-13
run
> 
gksu software-properties-gtk

from cli and post the errors you get here

That command does the same as opening "Software Sources" from the "System" menu.

---

### Post by Bobrm2 on 2009-09-13
> **biebel said:**
> run

from cli and post the errors you get here

That command does the same as opening "Software Sources" from the "System" menu.

Ran, Terminal, (don't understand "cli") as You suggested, Software Sources opened to first tab, and locked up??

---

### Post by arrange on 2009-09-13
Run these commands one by one```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
sudo apt-get dist-upgrade
```

If you see any errors, stop there and COPY the output of the command (including the command) here.

---

### Post by biebel on 2009-09-13
cli = commandline interface = terminal

If there were error messages in the terminal window while it locked up post them here.

If not make a backup of sources.lst files, delete the original and try again
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
gksu software-properties-gtk

```

---

### Post by Bobrm2 on 2009-09-13
Arrange, All commands ran without error?

---

### Post by Bobrm2 on 2009-09-13
bob@Bob:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bob@Bob:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bob@Bob:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
bob@Bob:~$ gksu software-properties-gtk
could not open file '/etc/apt/sources.list'
could not open file '/etc/apt/sources.list'




> **biebel said:**
> cli = commandline interface = terminal

If there were error messages in the terminal window while it locked up post them here.

If not make a backup of sources.lst files, delete the original and try again
```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
gksu software-properties-gtk

```

---

### Post by arrange on 2009-09-13
Put the backup back and try Synaptic from Terminal instead, if that will spit out some more helpful output.```
sudo mv /etc/apt/sources.list.bak /etc/apt/sources.list
gksudo synaptic
```

---

### Post by biebel on 2009-09-13
That errormsg is normal as you just removed that file. Can you access any other tab now without the sources.lst?

If you can just go through the tabs, configure as you like and close. Especially the ubuntu software tab needs to be configured. When you click close after making a change it should generate a new sources.lst files with the jaunty repos.
Run the commands arrange posted again and see if that fixed your problem.

@arrange: Looking at his sources.list the file itself is part of the problem.

I'm going to let you handle this one now, because the two of us trying to help will only cause confusion.

---

### Post by arrange on 2009-09-13
> **biebel said:**
> @arrange: Looking at his sources.list the file itself is part of the problem.

I'm going to let you handle this one now, because the two of us trying to help will only cause confusion.

Sorry, I saw you not responding for about 30 mins so I thought I would have a go :)

His *sources.list* could be a problem but then I think *apt-get update* would have complained in the first place.

---

### Post by Bobrm2 on 2009-09-13
# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted

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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
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
deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
#deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) jaunty main
#eb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) jaunty main
deb [http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu) jaunty main



##
deb [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/exaile-devel/ppa/ubuntu](http://ppa.launchpad.net/exaile-devel/ppa/ubuntu) jaunty main

---

### Post by Bobrm2 on 2009-09-13
> **biebel said:**
> That errormsg is normal as you just removed that file. Can you access any other tab now without the sources.lst?

If you can just go through the tabs, configure as you like and close. Especially the ubuntu software tab needs to be configured. When you click close after making a change it should generate a new sources.lst files with the jaunty repos.
Run the commands arrange posted again and see if that fixed your problem.

@arrange: Looking at his sources.list the file itself is part of the problem.

I'm going to let you handle this one now, because the two of us trying to help will only cause confusion.

Can only get to "Software Sources" through /system/Administration/Update Manager. There I can change tabs and select items as I wish. Have re-ran dpkg --configure -a etc.  Still no ability (from the panel) to select software tools, Syanptic, Add/remove; varioius others that have to do with and coming form /root directories, i.e. sudo gksudo etc. There is a feeling of improvement; maybe speed I'm not for sure.  Thanks for your time and assistance

Bob

---

### Post by arrange on 2009-09-13
Picking two of the programmes you write that don't work: could you try```
gksudo gdmsetup --debug
gksudo synaptic --debug
```Post any output here + are those programmes (gdmsetup="Login window", Synaptic) working?

---

### Post by Bobrm2 on 2009-09-13
have re-started this box several times this morning.

---

### Post by Bobrm2 on 2009-09-13
> **arrange said:**
> Picking two of the programmes you write that don't work: could you try```
gksudo gdmsetup --debug
gksudo synaptic --debug
```Post any output here + are those programmes (gdmsetup="Login window", Synaptic) working?
bob@Bob:~$ gksudo synaptic --debug
No ask_pass set, using default!
xauth: /tmp/libgksu-31vwmI/.Xauthority
STARTUP_ID: gksudo/synaptic/4825-0-Bob_TIME1137216
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: synaptic
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
bob@Bob:~$ gksudo gdmsetup --debug
No ask_pass set, using default!
xauth: /tmp/libgksu-lZYCvZ/.Xauthority
STARTUP_ID: gksudo/gdmsetup/4874-0-Bob_TIME1288577
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: gdmsetup
buffer: -GNOME_SUDO_PASSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...

---

### Post by Bobrm2 on 2009-09-13
Login Window Preferences is not responding; although it did appear on the desktop.  Synaptic has the same condition.

---

### Post by biebel on 2009-09-13
This may be a long shot, but if it works it's a shortcut:
```

sudo apt-get install --reinstall synaptic update-manager

```

That will reinstall those packages and with some luck fix your problem or give errormsgs that might help.

---

### Post by Bobrm2 on 2009-09-13
> **biebel said:**
> This may be a long shot, but if it works it's a shortcut:
```

sudo apt-get install --reinstall synaptic update-manager

```

That will reinstall those packages and with some luck fix your problem or give errormsgs that might help.

No Joy here; following error received:
"Synaptic" is not responding.

You may choose to wait a short while for it to continue or force the application to quit entirely.

Why do I have two different startup screens? or sometimes when I restart the other login screen appears. I don't even know which screen (startup) I'm working behind. Another words, do I think that I'm repairing one while actually involved with another "user". Bob = bob = bob. Very confused.
Users in User/Groups are: root, bob, and bob1(added this afternoon; however the confusion existed prior to it's addition.>>???:confused:

---

### Post by biebel on 2009-09-13
It does seem more and more like a permissions / user / password problem than a problem with a package that is showing symptoms.

Do you get propmted for your password when gksudoing?

If not just use sudo
```

sudo synaptic

```
That way you get prompted for your password in the terminal.

[edit]
I'm using [code] [/quote] so I think it's time to get some sleep
[/edit]

---

### Post by Bobrm2 on 2009-09-13
Well, I just, to prove it, ran gksu synaptic. The password screen popped up, I supplied the necessary password, then was informed that another Synaptic was running (where) and it was trying to be brought forward. The hidden file never came forward?? It is late and Jimmy Stewart is on the movie channel, thank you appreciate your help. Wait, the other(?) user just and involuntarily came up, I have to log back in. I need to figure out how to get rid of one user, but can't get into /system/administration/user and groups (open but grayed out).

Thanks

---

### Post by ZenLord422 on 2009-10-07
I have the  same problem. Nothing to add  I went thru terminal no response. Ubuntu jaunty (wubi install) Can't update , synaptic wont launch, add/remove ---->WONT Work uuuugggggghHHHH!!!!

---

