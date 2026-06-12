---
title: "Kde ??? !!"
date: 2006-02-08
forum: Desktop Environments
---

### Post by Seinfeld on 2006-02-08
Has anyone lately tried to install KDE on Ubuntu Breezy ?? I get a dependency error now 
================================

 $apt-get install kde
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kdeaddons but it is not going to be installed
       Depends: kdesdk but it is not going to be installed
E: Broken packages :???: 

Help ??

---

### Post by dcast on 2006-02-08
try it with synaptic do you have the right repositories enabled?

---

### Post by Seinfeld on 2006-02-08
Yes.. I tried again..

Actually I had the official Debian testing repos there too, but I removed it, and made sure all Ubuntu repos are there, Breezy, Updates and Security.. 

I did apt-get update.. and tried again.. things are better now, but still only one dependency problem

kde: Depends: kdesdk but it is not going to be installed

Am I missing something ???:rolleyes:

---

### Post by BlackJack on 2006-02-08
I did it the other day with the following command with no problems.

sudo apt-get install kubuntu-desktop

Hope this helps...........

---

### Post by Seinfeld on 2006-02-10
Thanks my friend.. It worked but I wonder why the kde does not. Isn't it just the same thing ??

Well, I do have some dependency problems rising too frequent lately.  For example, I do have it now in gcc. It complains for gcc-4 dependency. 
When i go for it, it complains
gcc-4.0:
  Depends: gcc-4.0-base (=4.0.1-4ubuntu9) but 4.0.2-5 is to be installed
  Depends: cpp-4.0 (=4.0.1-4ubuntu9) but 4.0.2-5 is to be installed

So, how can I just now the way around these unavailable dependencies, am I missing something ? or this is just a temporary repository problem and I should try later ??

Thanks a lot :)

---

### Post by aysiu on 2006-02-10
I'm with **dcast** on this one.
Can you post the output of this command? ```
cat /etc/apt/sources.list
``` If you're getting that error, it's usually because you have conflicting repositories.

---

### Post by Seinfeld on 2006-02-10
Thanks a lot guys..

The "sources.list" file is intact I think. Anyways, here is your request and thanks in advance 
============================================
## Uncomment the following two lines to fetch updated software from the network
#deb-src [http://eg.archive.ubuntu.com/ubuntu](http://eg.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://eg.archive.ubuntu.com/ubuntu](http://eg.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
#deb-src [http://eg.archive.ubuntu.com/ubuntu](http://eg.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://eg.archive.ubuntu.com/ubuntu](http://eg.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
#deb-src [http://eg.archive.ubuntu.com/ubuntu](http://eg.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://eg.archive.ubuntu.com/ubuntu](http://eg.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb-src [http://eg.archive.ubuntu.com/ubuntu](http://eg.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
================================================
Thanks a lot.. Please have a look at my last postings in the thread regrading my sources.list problem under the title "Adding Debian Repositories" at [http://ubuntuforums.org/showthread.php?t=126566&page=2](http://ubuntuforums.org/showthread.php?t=126566&page=2) . 
It may shed some light and you may give me advice as well in this issue. It is realy annoying, maybe I couldn't retrieve the file as it should be because of this problem..

Thanks a lot

---

