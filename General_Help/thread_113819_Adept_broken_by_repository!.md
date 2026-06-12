---
title: "Adept broken by repository!"
date: 2006-01-07
forum: General Help
---

### Post by Mathias-K on 2006-01-07
Hi fellow Kubuntuers..

I was updating my Kubuntu 5.10 i386 install with OpenOffice 2.0.1, when I thought that I'd like a completely up to date KDE 3.5, so i browsed Kubuntu.org and found this site --> [http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

I then added this line "deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main" to my repositories in Adept, and tried to run it. The program crashed, and now i get this error trying to open it:

"The APT Database could not be opened! This may be caused by incorrect APT configuration or something similar. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem."

I tried running both sudo apt-setup and sudo apt-get update, but i haven't had any luck getting it to work. Any ideas what to do? And couldn't Adept just tell me to delete the line and continue working properly?

---

### Post by nandasunu on 2006-01-07
I had this same problem upgrading to kde 3.5 and adding the repo with adept.

if you can paste your /etc/apt/sources.list here I can see if it is the same thing I had. Its probably that instead of entering the new repo in at the bottom of the file, it has overwritten part of the top of the file and corrupted it.

---

### Post by Mathias-K on 2006-01-07
Hi, I'm happy to hear that I'm not the only one, though i think that this reaction is stupid and a blow to KDE user friendliness. > deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted ## Major bug fix updates produced after the final release of the ## distribution. deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted ## Uncomment the following two lines to add software from the 'universe' ## repository. ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu ## team, and may not be under a free licence. Please satisfy yourself as to ## your rights to use the software. Also, please note that software in ## universe WILL NOT receive any review or updates from the Ubuntu security ## team. deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe ## Uncomment the following two lines to add software from the 'backports' ## repository. ## N.B. software from this repository may not have been tested as ## extensively as that contained in the main release, although it includes ## newer versions of some applications which may provide useful features. ## Also, please note that software in backports WILL NOT receive any review ## or updates from the Ubuntu security team. ## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse ## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./ ## deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free ## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi ## deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse ## created by arnieplanetremoved 

Trying to right-click-copy the text, i saw 'edit as root', and by removing the line i added, it now works again :)

Why on earth has the developers made it that weird? :(

---

### Post by nandasunu on 2006-01-07
glad you got it working, I guess it must be a bug (feel like submitting a bug report?)

---

### Post by ace2005 on 2006-01-07
You might want to try doing  updates to KDE from Fluxbox in Synaptic, so far for me everything has worked fine

Just out of curiosity how would adept update itself?

---

