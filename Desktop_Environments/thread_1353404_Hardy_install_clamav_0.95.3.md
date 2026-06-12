---
title: "Hardy install clamav 0.95.3"
date: 2009-12-12
forum: Desktop Environments
---

### Post by dgermann on 2009-12-12
Hi--

I have two Hardy boxes, both running 8.04. On one I can use apt-get to install clamav and clamav-daemon, both version 0.95.3. On the other, the most I can get is version 0.94.

Of course, when I go to run freshclam on the second machine it tells me the version I have is out of date.

So how do I get the correct version on the second machine, please?

Thanks!

:- Doug.

---

### Post by dgermann on 2009-12-14
Well, I managed to get that resolved, at least enough to install 0.95.3 and get it operating, I think. 

What I did: I changed my sources.list to read:
```
# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb http://archive.ubuntu.com/ubuntu/ hardy universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe multiverse


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse



deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main

```

Have set up a cron job for overnight, so we will see how well it runs.

---

### Post by unqtious on 2010-02-03
After several failed attempts to update using the new repositories outlined in the community documentation ([https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)), Clamav still says that I'm using an outdated version, which is version 9.4. And I accomplished every task outlined, including adding the openpgp key. Please advise on how to get 9.5 on my Hardy. 

I'm not upgrading to Karmic--what a pain in the tuckus. Hardy runs much better on my laptop.

---

### Post by dgermann on 2010-02-03
unqtious--

Carefully compare your /etc/apt/sources.list against what I have in my post 2 above and see what the differences are. (You can ignore the ones which are commented out--that is, where the line starts with #.) The one you are looking for should not be in the launchpad repos I have there.

Edit the file using gedit or your favorite editor to match the entries I have there.

Then from command line run sudo apt-get update, then sudo apt-get remove clamav. 

Once that is done do sudo apt-get install clamav, sudo apt-get install clamav-daemon and if you want it sudo apt-get install clamtk.

Please let us know your success or not. It worked for me, but ymmv, so no guarantees. I hope it works for you.

---

### Post by unqtious on 2010-02-26
Thank you much, dgermann. Adding from your list of repositories worked like a charm. Plus, it gave all sort of updates (security?) for several other programs. Cheers!

---

### Post by dgermann on 2010-02-28
unqtious--

Glad it worked for you!

Now, pass it on by helping someone else use Ubuntu (in life and in computers!).

---

### Post by kule on 2010-04-16
In case this is useful to anyone I did this:


```

> nano /etc/apt/sources.list

Add these two lines:
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse


> apt-get update
> apt-get install clamav-daemon
> clamd -V
ClamAV 0.95.3/10752/Fri Apr 16 15:32:36 2010



```

---

### Post by dgermann on 2010-04-16
Great!

Now here's the $96 question: how do you get 0.96?

---

### Post by unqtious on 2010-06-12
I reinstalled Ubuntu Hardy since the last problem. However, the ClamAV scanner updated to version .96 automatically once I got the repositories from the community documentation ([https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)). Then, almost after adding the key, a security update updated to 96.

---

### Post by dgermann on 2010-06-17
unqtious--

Thanks!

Do you mean you set up the PPA for your repository?

---

### Post by unqtious on 2010-06-18
Not PPA. When I installed the fresh version after a networking mishap, involving a DNS server, I used uploaded all the markings from the previous install. So, it was through the SPM.

---

### Post by dgermann on 2010-06-19
unqtious--

Sorry, still not following you. What is SPM?

I'm running 8.04. What are you using?

Thanks!

---

### Post by unqtious on 2010-06-23
Hi Doug,

Let me start by explaining what a noob I am--well, semi-noob. Or, maybe I'm noobish, or maybe that's supposed to be nebish. 

Anyway, I'm running 8.04.. 

Let's start over. I'm not sure about the ppas, but for the most part, I used synaptic package manager. This is how I installed ClamAV. While I had problems upgrading before when using the repositories, when I had to re-install Ubuntu--for God only knows why--the repositories worked for me. Whereas before they didn't. 

In short, I'm not sure if it helps you any, but you can try putting those same repositories ([https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)) into your etc/apt/source.list. Hopefully it will work for you as it had for me. 

Cheers!

---

### Post by dgermann on 2010-06-24
unqtious--

Thanks!

Somehow I am still missing something. :confused: I have the Universe repository enabled as they say, but still I get the error message about being out of date. And Synaptic shows its version as 0.95.3.

Could you post your sources.list file here? Or at least tell me if this line is in it?
> deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) hardy main

Thanks, unqtious!

---

### Post by unqtious on 2010-06-25
Sure thing. You'll notice that the last line is the ClamAV repository. I  use, as you may also notice, Bitdefender, which has a very nice GUI. But I read that ClamAV has the best information on viruses. 

[HTML]deb cdrom:[Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090713.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted
deb http://archive.ubuntu.com/ubuntu/ hardy restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates restricted multiverse

deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb http://download.bitdefender.com/repos/deb/ bitdefender non-free
deb http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu hardy main[/HTML]After I put this into the sources.list, I put into the terminal the following:

[HTML]sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xf80220d0e695a455e651ac4d8ab767895adc2037 
sudo apt-get update
sudo apt-get upgrade[/HTML]I hope this helps.

---

### Post by dgermann on 2010-06-27
unqtious--

Yes, that helps!

You do have ppa, and that is what enables you to get the 0.96 ```
version:deb http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu hardy main
```

So that explains it!

Thanks, unqtious!

I might just give that a try.

---

