---
title: "Wine won't install fully"
date: 2009-02-04
forum: General Help
---

### Post by FranticFinn on 2009-02-04
So I get to the part where I can see Wine 1.1.14 in the Synaptic Packet Manager. When I "mark for installation" I receive this message

"To be installed  libaudio2"

So I mark it for install and I then get the following:

"Wine: Depends: libasound2 (>1.0.17) but 1.0.15-3ubuntu4 is to be installed"

This looks oddly like I have a newer version of libasound2 than is being looked for to work with Wine. While I have been in computers for almost 15 years, I just popped my Ubuntu Cherry, so go easy ;)

Thanks in advance,

FranticFinn

---

### Post by adult swim on 2009-02-05
the libasound2 you need is newer than the one you have available in hardy.  you may have luck trying the intrepid version, which is what is specified.
[http://packages.ubuntu.com/intrepid/libasound2](http://packages.ubuntu.com/intrepid/libasound2)

---

### Post by FranticFinn on 2009-02-05
> **adult swim said:**
> the libasound2 you need is newer than the one you have available in hardy.  you may have luck trying the intrepid version, which is what is specified.
[http://packages.ubuntu.com/intrepid/libasound2](http://packages.ubuntu.com/intrepid/libasound2)

So I locate and try to install the 1.0.17 plugin and get the following from the package manager:

Error: "Wrong Architecture amd64"

At the risk of sounding stupid, I am running an AMD 6000x2 64bit Architecture...or does this refer to something else here? 

(Hair is beginning to fall out, ok with a lil' help)

---

### Post by adult swim on 2009-02-05
aer you installing 64bit wine?  if you are installing i386 wine, i think youll need the i386 libasound2 package.

---

### Post by Yellow Pasque on 2009-02-05
> So I get to the part where I can see Wine 1.1.14 in the Synaptic Packet Manager.

You're running Ubuntu 8.04.x/Hardy, correct?

It appears you went to WINE's site and added their repo, correct? Either  you added the wrong repo (i.e. the wrong release of Ubuntu) or there's something wrong with their .deb package.

You should not need to install packages from other releases (this is a good way to bork the package manager).

---

### Post by FranticFinn on 2009-02-05
I don't remember downloading anything from the Wine site (was the other day) I opened the Syn.Packet Mgr and scrolled down to the Wine 1.1.14 entry then clicked "mark for installation"

...so what should I do now...Did I hose something?

---

### Post by FranticFinn on 2009-02-05
I am pretty sure I installed the 64bit version. (don't know if it matters but..)
In order, I installed Ubuntu from disk then upgraded to Hardy 8.04 then tried to get Wine for 64.
Anyways, I attempted to download the 386 and it would not allow it, backing up my recolection that I had instaled the 64bit Ubuntu

---

### Post by Yellow Pasque on 2009-02-05
WINE 1.1.14 isn't even found in the current development release of Ubuntu, so you must have some 3rd-party repo installed. (Ubuntu uses the "stable" 1.0x branch of WINE in their standard repos)

What is the output from:
```
cat /etc/apt/sources.list
```

---

### Post by FranticFinn on 2009-02-05
dad@dad-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 &#8220;Intrepid Ibex&#8221;
dad@dad-desktop:~$ 

Easy does it...this is my first day....lol (sorry copy/paste was the only way I know to bring it here)

If I am not mistaken... The CD I originally obtained looks like it was 386, no? Then I upgraded to Hardy and chose 64 bit.. (but no warnings popped up at the time) but might explain alot here....

---

### Post by Yellow Pasque on 2009-02-05
> deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 &#8220;Intrepid Ibex&#8221;
This line is your problem. It is for the wrong version of Ubuntu.
Close Synaptic or Update Manager if they're open and go to System -> Administration -> Software Sources
Go to the "Third-Party Software" tab, select the line for the wine repo and click 'Remove'. Now click 'Add' and paste this in:
```
deb http://wine.budgetdedicated.com/apt hardy main
```
Click "Add Source" and close. A prompt will come up asking you to update your package list or something (say Yes).
Now you can go into Synaptic and install wine.

---

### Post by FranticFinn on 2009-02-05
Good Show !!! Assistance is always appreciated by me. Thanks a million :D

The Finn

Now when I update to Intrepid, will all apps auto-update?

---

### Post by Yellow Pasque on 2009-02-05
You're welcome.
> Now when I update to Intrepid, will all apps auto-update?
Most of them, but not ones from the 3rd-party repos you added. 
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
> If you are upgrading the entire system, such as going from Ubuntu 8.04 to 8.10, you will need to come back to this page and add the repository for the new version above. The built in update manager will not switch the Wine repository automatically.

---

