---
title: "[SOLVED] gnome desktop"
date: 2007-10-19
forum: Desktop Environments
---

### Post by skyjacker on 2007-10-19
I currently have kubuntu  (Gutsy 7.10) which I downloaded and installed.  The new kde sucks, how can I get Gnome desk-top installed from kde?:confused:

---

### Post by ubuntu27 on 2007-10-19
Here is a guide:

[How to install GNOME when you are using Kubuntu?]("http://www.psychocats.net/ubuntu/gnome")

Short answer:

```
sudo aptitude install ubuntu-desktop
```

---

### Post by chemisus on 2007-10-19
> **skyjacker said:**
> I currently have kubuntu  (Gutsy 7.10) which I downloaded and installed.  The new kde sucks, how can I get Gnome desk-top installed from kde?:confused:

the only problem i have had with "the new kde" is that dolphin is the default file browser. other then that, i dont notice much difference between kde on gutsy and kde on feisty.

to make konqueror the default file browser on your system, just remove dolphin from the system:

```
sudo aptitude remove dolphin
```

---

### Post by skyjacker on 2007-10-20
> **ubuntu27 said:**
> Here is a guide:

[How to install GNOME when you are using Kubuntu?]("http://www.psychocats.net/ubuntu/gnome")

Short answer:

```
sudo aptitude install ubuntu-desktop
```
I tried the info from psychocats exactly, and instead of installing gde, it said the package could not be found. Also the same with aptitude command. Why can't I install gde? I don't like the fact that I cannot use evolution or Firefox in kde. Please HELP!:confused:

---

### Post by mortsahl on 2007-10-20
It's GDM not GDE

---

### Post by skyjacker on 2007-10-20
Here is the response I get when I try ANY code (aptitude or apt-get) in terminal to get GDM:
skyjacker@skyjacker-desktop:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find package "ubuntu-desktop".  However, the following
packages contain "ubuntu-desktop" in their name:
  kubuntu-desktop
The following packages have been kept back:
  tzdata
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
I would like to be able to get the Gnome desktop... Do I have to install Ubuntu just to get it? :confused:

Please help if you can

---

### Post by rsambuca on 2007-10-20
There must be something wrong with your repositories.  Post the output of 

cat /etc/apt/sources.list

---

### Post by skyjacker on 2007-10-20
> **rsambuca said:**
> There must be something wrong with your repositories.  Post the output of 

cat /etc/apt/sources.list
Here it is. Hope you can help...
skyjacker@skyjacker-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

---

### Post by rsambuca on 2007-10-20
Some of your repositories got automatically removed because they failed to verify.  It is probably due to the overloaded servers at the moment (from the Gutsy release).  Remove the number sign '#' from the lines I have highlighted in red.  You can do this in a text editor by entering the following command```
gksudo gedit /etc/apt/sources.list
```
```
deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
[COLOR="Red"]# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted[/COLOR]
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
[COLOR="Red"]# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse[/COLOR]
# Line commented out by installer because it failed to verify:
[COLOR="Red"]# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse[/COLOR]

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
```Save the file, exit, then run a 'sudo apt-get update'.  Then try your ubuntu-desktop installation again.  Keep in mind that the servers are quite busy, so it may take quite a while.

---

### Post by skyjacker on 2007-10-20
rsambuca, here is what I got when I typed the gksudo line in terminal:

skyjacker@skyjacker-desktop:~$ gksudo gedit /etc/apt/sources.list
The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found
skyjacker@skyjacker-desktop:~$ sudo apt-get install gksu
[sudo] password for skyjacker:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package gksu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gksu has no installation candidate

What do I do now??:confused:

---

### Post by ubuntu27 on 2007-10-20
> **skyjacker said:**
> rsambuca, here is what I got when I typed the gksudo line in terminal:

skyjacker@skyjacker-desktop:~$ gksudo gedit /etc/apt/sources.list
The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found
skyjacker@skyjacker-desktop:~$ sudo apt-get install gksu
[sudo] password for skyjacker:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package gksu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gksu has no installation candidate

What do I do now??:confused:

Do this:

```
sudo kwrite /etc/apt/sources.list
```

[Explanation of the command:  Execute  file called source.list which is located at /etc/apt/   with the program called kwrite]

if the above dosn't work do this:

```
sudo kedit /etc/apt/sources.list
```

Explanation: Execute  file called source.list which is located at /etc/apt/   with the program called kedit


After source.list is open, do what rsambuca said. :)

---

### Post by rsambuca on 2007-10-20
Sorry, I forgot you are running KDE and not Gnome.  Just use

kdesu kate /etc/apt/sources.list

---

### Post by skyjacker on 2007-10-21
It worked! Thanks to everyone for the help. Now I have only one more hurdle to cross and I will be back to where I was in Fiesty.:)

---

