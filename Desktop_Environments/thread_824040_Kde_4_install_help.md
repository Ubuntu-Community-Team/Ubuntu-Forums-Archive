---
title: "Kde 4 install help"
date: 2008-06-09
forum: Desktop Environments
---

### Post by N3um0rin on 2008-06-09
Can someone give me the sudo apt-get thingy to upgrade to kde 4? Please?

---

### Post by inportb on 2008-06-09
The package is called *kubuntu-kde4-desktop*:
*sudo apt-get install kubuntu-kde4-desktop*

However, that installs KDE 4.0.5. If you want KDE 4.1 beta 1 (a development version that has more features and maybe more bugs), check this:
[http://kubuntu.org/announcements/kde-4.1beta1.php](http://kubuntu.org/announcements/kde-4.1beta1.php)
and this for more information: [http://blog.nixternal.com/2008.06.05/hardy-kde-41-beta-1-completed/](http://blog.nixternal.com/2008.06.05/hardy-kde-41-beta-1-completed/)

---

### Post by N3um0rin on 2008-06-09
> **inportb said:**
> The package is called *kubuntu-kde4-desktop*:
*sudo apt-get install kubuntu-kde4-desktop*

However, that installs KDE 4.0.5. If you want KDE 4.1 beta 1 (a development version that has more features and maybe more bugs), check this:
[http://kubuntu.org/announcements/kde-4.1beta1.php](http://kubuntu.org/announcements/kde-4.1beta1.php)
and this for more information: [http://blog.nixternal.com/2008.06.05/hardy-kde-41-beta-1-completed/](http://blog.nixternal.com/2008.06.05/hardy-kde-41-beta-1-completed/)


Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package kubuntu-kde4-desktop

I think somthing went wrong..=\

---

### Post by inportb on 2008-06-09
> **N3um0rin said:**
> I think somthing went wrong..=\

I think something went wrong too. We need to know something about your setup. Are you using Ubuntu with KDE 3.5.x now? Also, can you please post the contents of your /etc/apt/sources.list file?

---

### Post by N3um0rin on 2008-06-09
> **inportb said:**
> I think something went wrong too. We need to know something about your setup. Are you using Ubuntu with KDE 3.5.x now? Also, can you please post the contents of your /etc/apt/sources.list file?
Ehg im using Kde 3.5.8
I just downloaded off of the old kubuntu livecd a few mins ago..Before that i had ubuntu and kde on it along with xubuntu but when i tried to get kde 4 ....manualy i screwed it up and ended up reloading..Lol

---

### Post by N3um0rin on 2008-06-09
And im still kinda a n00b ..

I cant find /etc/apt/sources.list ..But im probably doing somthing wrong

---

### Post by inportb on 2008-06-09
Okay, so if you *just* installed Kubuntu (or any Ubuntu), you most likely have not updated your package listing yet. Do this before running the installation command:

*sudo apt-get update*

Then when you're done, try installing KDE 4:

*sudo apt-get install kubuntu-kde4-desktop*

/etc/apt/sources.list is the path to the file. You can open it in kate by running:

*kdesu kate /etc/apt/sources.list*

But see if the installation works before messing with your sources.list file.

---

### Post by N3um0rin on 2008-06-09
> **inportb said:**
> Okay, so if you *just* installed Kubuntu (or any Ubuntu), you most likely have not updated your package listing yet. Do this before running the installation command:

*sudo apt-get update*

Then when you're done, try installing KDE 4:

*sudo apt-get install kubuntu-kde4-desktop*

/etc/apt/sources.list is the path to the file. You can open it in kate by running:

*kdesu kate /etc/apt/sources.list*

But see if the installation works before messing with your sources.list file.

Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


Wow its just full of problems today isnt it? ..

---

### Post by N3um0rin on 2008-06-09
> **N3um0rin said:**
> Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


Wow its just full of problems today isnt it? ..
I tried it again and got this 

Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by inportb on 2008-06-09
Oh, it's no wonder you couldn't find it; you're still running Gutsy.

If you don't mind reinstalling, I would suggest installing the latest and greatest Hardy Heron, which has a KDE 4 version: [http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php)

If you want to stick with Gutsy, do this: [http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)
You might want to read the error message and run *dpkg --configure -a* to fix your system. If you continue to get the message regarding /var/lib/dpkg/lock even if you don't have any apt/dpkg processes running, you can delete that file and try again.

---

### Post by N3um0rin on 2008-06-09
> **inportb said:**
> Oh, it's no wonder you couldn't find it; you're still running Gutsy.

If you don't mind reinstalling, I would suggest installing the latest and greatest Hardy Heron, which has a KDE 4 version: [http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php)

If you want to stick with Gutsy, do this: [http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)
You might want to read the error message and run *dpkg --configure -a* to fix your system. If you continue to get the message regarding /var/lib/dpkg/lock even if you don't have any apt/dpkg processes running, you can delete that file and try again.ARRGHH idid that and it keeps saying its being used by another process or adpt manager is already running and it isnt..i even restarted and its still doing it..>=[ HELP!!

---

### Post by inportb on 2008-06-09
Okay then, try deleting the lock file:
*sudo rm /var/lib/dpkg/lock*

then try whatever you were doing again.

---

### Post by N3um0rin on 2008-06-09
OK..So i did that..and it deleated it..Now ill try to open adpt manager again..Lol..>.< 
Thanks for helping me by the way =]

---

### Post by N3um0rin on 2008-06-09
> **inportb said:**
> Okay then, try deleting the lock file:
*sudo rm /var/lib/dpkg/lock*

then try whatever you were doing again.

I got this After i did the deleate thing..=[

Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself.

---

### Post by inportb on 2008-06-09
Hm... interesting... lemme do a quick search on that.

---

### Post by N3um0rin on 2008-06-09
> **inportb said:**
> Hm... interesting... lemme do a quick search on that.ok =] Thanks again for helping me..

---

### Post by inportb on 2008-06-09
no problem!

Let's try a different trick. *fuser* is able to kill all processes using a file. So let's make sure nothing's using /var/lib/dpkg/lock:
*sudo fuser -vki /var/lib/dpkg/lock*

then let's try this again:

*sudo dpkg --configure -a*

---

### Post by N3um0rin on 2008-06-09
> **inportb said:**
> no problem!

Let's try a different trick. *fuser* is able to kill all processes using a file. So let's make sure nothing's using /var/lib/dpkg/lock:
*sudo fuser -vki /var/lib/dpkg/lock*

then let's try this again:

*sudo dpkg --configure -a*
OK this is what i got ..=\

Setting up libc6 (2.6.1-1ubuntu9) ...

Setting up ipppd (1:3.10.20070306-0ubuntu3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing ipppd (--configure):
 subprocess post-installation script returned error exit status 1
Setting up mouseemu (0.15-8ubuntu1) ...
Creating /dev/input/uinput...udev active, devices will be created in /dev/.static/dev/
done.
 * Starting mouse emulation daemon mouseemu                              [ OK ]

Setting up eagle-usb-utils (2.1.1-3ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing eagle-usb-utils (--configure):
 subprocess post-installation script returned error exit status 1
Setting up capiutils (1:3.10.20070306-0ubuntu3) ...
Note: running MAKEDEV to create CAPI devices in /dev...
udev active, devices will be created in /dev/.static/dev/

Setting up oem-config (1.23) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing oem-config (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libstdc++6-4.1-dev (4.1.2-16ubuntu2) ...
Setting up g++-4.1 (4.1.2-16ubuntu2) ...
Setting up g++ (4:4.1.2-9ubuntu2) ...

dpkg: dependency problems prevent configuration of oem-config-kde:
 oem-config-kde depends on oem-config; however:
  Package oem-config is not configured yet.
dpkg: error processing oem-config-kde (--configure):
 dependency problems - leaving unconfigured
Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ipppd
 eagle-usb-utils
 oem-config
 oem-config-kde

---

### Post by Xiong Chiamiov on 2008-06-09
Press ctrl-esc to open the process table and do a search for (and kill) anything matching adept or synaptic.

You don't really have to redownload Hardy if you're running Gutsy; just make sure everything's updated, then run a dist-upgrade.  It'll download and install the appropriate packages.  That said, if you don't have anything invested on this, you might be better off downloading Hardy and reinstalling, since some people have had problems with the upgrade.
```

sudo -s
aptitude update; aptitude full-upgrade; aptitude dist-upgrade; exit

```

EDIT: BTW, if you're curious, "sudo -s" starts a root shell (so you don't have to continually type sudo this and sudo that), and the exit command at the end will return you to your normal user shell, so you don't accidentally do something bad.

---

### Post by N3um0rin on 2008-06-09
Uh..ALRIGHT =D The adpt thingy is working but NOw when i do the virsion upgrade thingy it ubuntu..Not kubuntu..Ehg..And id do the whole daownloading the iso and stuff but i dont have any cd's to burn it to..Ehg

---

### Post by N3um0rin on 2008-06-09
Which ever is easiest..Without having to burn cd's..I dont have any =[

---

### Post by Xiong Chiamiov on 2008-06-09
> **N3um0rin said:**
> Uh..ALRIGHT =D The adpt thingy is working but NOw when i do the virsion upgrade thingy it ubuntu..Not kubuntu..Ehg..And id do the whole daownloading the iso and stuff but i dont have any cd's to burn it to..Ehg
You could follow [this graphical procedure]("https://help.ubuntu.com/community/HardyUpgrades/Kubuntu") if you like.  Just scroll down a bit to where it says "over the internet".

I don't believe that there is any harm in it saying that you're downloading Ubuntu Hardy, since they are the same.  The only difference is in the meta-package that's installed with it (kubuntu-desktop vs. ubuntu-desktop).  As long as it doesn't try to install GNOME, you're fine.

---

### Post by inportb on 2008-06-09
Yep, that's right. This'll download and install quite a bit of stuff, so after you start the process, you can go take a break ;p

Post if you have questions/problems, or when you're done so we can work on getting KDE 4 (kubuntu-kde4-desktop).

---

### Post by N3um0rin on 2008-06-09
alright ill do that and then download kde4 with the pakage manager thingy..Thanks lots =]

---

### Post by Xiong Chiamiov on 2008-06-09
Don't know if you're asking inportb or me, but I'm glad to be of assistance.  I have a final from 7-10 tonight (now being 6 in my timezone), but I'll check back in after that if you don't have it solved before then.

---

### Post by N3um0rin on 2008-06-09
Both I guess..lol

But ok =] COFFEE BREAK!!!!

---

### Post by inportb on 2008-06-09
Sure thing. And I'll be back in a couple of hours (ge3kz gotta dine too, lolol)

---

### Post by N3um0rin on 2008-06-09
So far there are alot of errors..and ive only started..arhg

Im not posting every single one because htere's one every second but most of them have somthing to do with some dependency problem...

---

### Post by N3um0rin on 2008-06-09
I guess like you said i can expect problems.
I think ive done this before..The whole upgrading to this virsion..But i never had errors like this =\

---

### Post by inportb on 2008-06-09
> **N3um0rin said:**
> I guess like you said i can expect problems.
I think ive done this before..The whole upgrading to this virsion..But i never had errors like this =\

Ah, please post them, or as much as you can.

---

### Post by N3um0rin on 2008-06-09
Thats like that stupid free laptop commercial that they dont have anymore..>=[

---

### Post by inportb on 2008-06-09
Yeah... I reported it to mods XD

---

### Post by N3um0rin on 2008-06-09
Its hard to...you cant copy and paste the names of the thingys..that have...errors..lol

One is a dependancy problem another is a subprocess pre-installation script returned error exit status 1 thingy..Uh ooo and a PRE-dependency problem pre-dependency problem - not installing openoffice.org-base-core 
pre-dependency problem - not installing openoffice.org-impress
pre-dependency problem - not installing openoffice.org-draw
pre-dependency problem - not installing openoffice.org-math
pre-dependency problem - not installing openoffice.org-java-common
pre-dependency problem - not installing python-uno
pre-dependency problem - not installing openoffice.org-writer
pre-dependency problem - not installing openoffice.org-calc
pre-dependency problem - not installing openoffice.org-kde
pre-dependency problem - not installing openoffice.org-l10n-en-za
pre-dependency problem - not installing openoffice.org-core
pre-dependency problem - not installing openoffice.org-l10n-en-gb
pre-dependency problem - not installing openoffice.org-help-en-gb
pre-dependency problem - not installing openoffice.org-help-en-us
pre-dependency problem - not installing openoffice.org-l10n-common
pre-dependency problem - not installing openoffice.org-style-human
pre-dependency problem - not installing openoffice.org-style-crystal
pre-dependency problem - not installing openoffice.org-common
pre-dependency problem - not installing ttf-opensymbol
subprocess new post-removal script returned error exit status 1
subprocess new post-removal script returned error exit status 1
dependency problems - leaving unconfigured
dependency problems - leaving unconfigured
dependency problems - leaving unconfigured
Alright now two errors and i got this
 Window with title "Error " is not responding. This window belongs to application dist-upgrade.py (PID=10909, hostname=localhost).
Do you wish to terminate this application? (All unsaved data in this application will be lost.)

---

### Post by N3um0rin on 2008-06-09
lotsss of errors..=\ I guess i start over ne?

---

### Post by N3um0rin on 2008-06-09
Great i got the whole another packaging thingy is running error all over again..D=<

---

### Post by N3um0rin on 2008-06-09
Do you think i should reload again? I hate doing it..but maybe i should...

---

### Post by inportb on 2008-06-09
What do you mean by reload again?

Also, what happened that got you into the first apt problem? I have a feeling it might give us some clues.

---

### Post by N3um0rin on 2008-06-09
Uhm..I dont really know..I x'ed out because i didnt think i was using the right program and i think thats when it happened..And i mean re-install kubuntu and see if it all goes away

---

### Post by inportb on 2008-06-09
Well, if you don't mind making backups and all that, I think it might be the best way to go. The reason is that the system might be in an inconsistent state that might take more than 20 minutes (the time it takes to install) to sort out.

If you do decide to reinstall Gutsy, perform the upgrade right after, before doing anything else. You can use this guide linked by Xiong:
[https://help.ubuntu.com/community/HardyUpgrades/Kubuntu](https://help.ubuntu.com/community/HardyUpgrades/Kubuntu)

---

### Post by N3um0rin on 2008-06-10
I ended up installing ubuntu instead of kde ..Ill add on kde like i did before and then update that..Does anyone have the sudo apt-get thingy to get it?

---

### Post by inportb on 2008-06-10
Same as said at the beginning of the thread ;p

For Gutsy:
[http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

For Hardy:
[http://kubuntu.org/announcements/kde-4.0.5.php](http://kubuntu.org/announcements/kde-4.0.5.php)
[http://kubuntu.org/announcements/kde-4.1beta1.php](http://kubuntu.org/announcements/kde-4.1beta1.php)

---

### Post by N3um0rin on 2008-06-10
But dont you have to atleast have kubuntu installed? =\ I may be wrong..

---

### Post by N3um0rin on 2008-06-10
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

I got it from here =] I think this is the same thing i did before too...I feel so smart >.<

---

### Post by Xiong Chiamiov on 2008-06-10
> **N3um0rin said:**
> But dont you have to atleast have kubuntu installed? =\ I may be wrong..
Kubuntu is Ubuntu with KDE instead of GNOME.  Since the KDE4 installation installs KDE4 separately (not upgrading 3.5), it doesn't matter if you have KDE 3.5 installed or not.

Installing the kubuntu-desktop package will install KDE 3.5.  If you want KDE4 (which, from the title of this thread, I'm guessing you do), then follow the instructions inportb gave.

---

### Post by N3um0rin on 2008-06-10
mkay =]

---

### Post by N3um0rin on 2008-06-10
I did what it said on that link you gave me and it keeps saying it cant install it because it will "break"..something like that

---

### Post by N3um0rin on 2008-06-10
My hamster is probably better at this than me =[

---

### Post by inportb on 2008-06-10
No worries; let's try to figure this out.

Which version of KDE 4 are you installing? (i.e. which link are you following?)

---

### Post by N3um0rin on 2008-06-10
[http://kubuntu.org/announcements/kde-4.0.5.php](http://kubuntu.org/announcements/kde-4.0.5.php)

this one

---

### Post by inportb on 2008-06-10
Okay, great. I'm assuming you are now running Ubuntu 8.04 and have enabled the hardy-backports repository as described in the announcement.

Please pop open your terminal and type: (we make sure all packages are up-to-date and try to install KDE 4)

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kubuntu-kde4-desktop
```

Please paste the output of these commands. Thanks.

---

### Post by N3um0rin on 2008-06-10
should i do that on kde or gnome?

---

### Post by N3um0rin on 2008-06-10
> **inportb said:**
> Okay, great. I'm assuming you are now running Ubuntu 8.04 and have enabled the hardy-backports repository as described in the announcement.

Please pop open your terminal and type: (we make sure all packages are up-to-date and try to install KDE 4)

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kubuntu-kde4-desktop
```

Please paste the output of these commands. Thanks.

well this is what i got

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release [27.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Fetched 1B in 0s (1B/s)
Reading package lists... Done
namethingyhere:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  libqt4-core libqt4-gui
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
namethingyhere:~$ sudo apt-get install kubuntu-kde4-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package kubuntu-kde4-desktop

---

### Post by inportb on 2008-06-10
osnap. I think you have both gutsy and hardy packages. Let's see if we could fix that. Please post your /etc/apt/sources.list file:

kdesu kate /etc/apt/sources.list

---

### Post by N3um0rin on 2008-06-10
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main

---

### Post by inportb on 2008-06-10
Thanks. It appears that you're missing some Hardy repositories, and still have a Gutsy repository. I'd recommend replacing the contents of that file with this:

```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

This is what one would have gotten from a direct installation of Ubuntu 8.04, with backports enabled.

When you're done do this again:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kubuntu-kde4-desktop
```

---

### Post by N3um0rin on 2008-06-10
uh..ok hold on

I dont have permission to save it..

---

### Post by inportb on 2008-06-10
Oh, hm. You gotta open up that file with superuser privileges, like:

*kdesu kate /etc/apt/sources.list*

or

*sudo kate /etc/apt/sources.list*

---

### Post by N3um0rin on 2008-06-10
> **inportb said:**
> Oh, hm. You gotta open up that file with superuser privileges, like:

*kdesu kate /etc/apt/sources.list*

or

*sudo kate /etc/apt/sources.list*
ehg..i knew that 
>.<..really

---

### Post by inportb on 2008-06-10
hehe, let us know how it goes. It may update a bunch of packages. And it should be able to find the kubuntu-kde4-desktop package.

---

### Post by N3um0rin on 2008-06-10
Arhg!!! My internet cut out RIGHT in the middle of it!!! >=[ Its ok to start it over again isnt it?

---

### Post by inportb on 2008-06-10
Sure; it was most likely just downloading packages. Just redo your last command.

---

### Post by N3um0rin on 2008-06-10
Ok its done..Ill restart ..and hopefully kde 4 isnt TOO buggy..So i have every thing save incase i end up reloading if its too horrible..Lol Thanks for your help =]

---

### Post by inportb on 2008-06-10
No problem! When you login, select KDE 4 from the session list.

---

### Post by N3um0rin on 2008-06-10
Arhg!! Kde 4 didnt show up in the sessions list thingy..

Edit: When i restarted it updated and now im installing again and its working so far i think it'll install it this time

---

### Post by N3um0rin on 2008-06-10
Well im using it now and so far it crashed already once..Im waiting for it to happen again..but it is nice..im kinda..ehg about doing too much at once..i might blow it up..lol But i guess all i can do is keep reporting bugs until its usable =]

edit: Nvm it already did

---

### Post by inportb on 2008-06-10
lol, it happens. KDE 4.1 beta 1 has been strangely stable for me, though it's a development version.

---

### Post by N3um0rin on 2008-06-10
Maybe i should try it? It wouldent hurt..

---

### Post by inportb on 2008-06-11
It does have the potential to be more unstable, because it's a beta. But if you're feeling particularly adventurous... it's got quite a few new features.

---

### Post by 24/7 on 2009-02-17
wow.... you had so many problems..... have*..... mine all worked straight away... i feel sorry for you.... lol... just more proof of how great the Ubuntu community is to support people even through all these problems you're having!

---

### Post by Xiong Chiamiov on 2009-02-17
> **24/7 said:**
> wow.... you had so many problems..... have*..... mine all worked straight away... i feel sorry for you.... lol... just more proof of how great the Ubuntu community is to support people even through all these problems you're having!
[Thread necromancy](http://en.wiktionary.org/wiki/thread_necromancy).

---

