---
title: "update issue"
date: 2009-03-12
forum: General Help
---

### Post by Froodolt on 2009-03-12
Hi all,

I have an update issue.
Installed Ubuntu 8.10 in dual-boot a few weeks ago. 
I have a working internet connection (otherwise I wouldn't be able to post this).

I keep having the orange triangle pop-up on the panel in the right upper corner. 
Update-manager says that the package information isn't updated for 14 days.
When I press the check button I get the following message (in Dutch because I have my language set to Dutch): 
“GPG-fout: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: De volgende ondertekeningen konden niet geverifieerd worden omdat de publieke sleutel niet beschikbaar is: NO_PUBKEY 7D2C7A23BF810CD5Ophalen van [http://apt.emesene.org/./Sources.gz](http://apt.emesene.org/./Sources.gz) 404 Not Found is mislukt

Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.”
Is it only an emesene problem or is my whole system not up to date?

When I close the waring, noting happens.
It keeps telling me that the package information is old and updated 14days ago.

I tried to Google a solution, but nothing I could fined worked for me. 
Selected other update server, didn't work.
Deselected all the update manager settings, rebooted and checked the selection boxes on again, didn't work.
I couldn't find an answer in this forum, so it must be something wrong with my settings or something.

Does someone have an idea how to solve this? :-k

Thanks in advance! 
:mrgreen:

---

### Post by Yellow Pasque on 2009-03-12
Please post output of:
```
cat /etc/apt/sources.list
```

---

### Post by Vadi on 2009-03-12
Go to System - Administration - Software Sources, click on the third-party software tab, and remove the line about emesene.org.

Then it should be able to update fine.

---

### Post by Froodolt on 2009-03-12
You guys are fast!!

@Temüjin: 
```
 bas@bas-laptop:~$ cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to

# newer versions of the distribution.





## Major bug fix updates produced after the final release of the

## distribution.



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team. Also, please note that software in universe WILL NOT receive any

## review or updates from the Ubuntu security team.



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

## team, and may not be under a free licence. Please satisfy yourself as to 

## your rights to use the software. Also, please note that software in 

## multiverse WILL NOT receive any review or updates from the Ubuntu

## security team.



## Uncomment the following two lines to add software from the 'backports'

## repository.

## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.

# deb http://nl.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

# deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse



## Uncomment the following two lines to add software from Canonical's

## 'partner' repository. This software is not part of Ubuntu, but is

## offered by Canonical and the respective vendors as a service to Ubuntu

## users.

# deb http://archive.canonical.com/ubuntu intrepid partner

# deb-src http://archive.canonical.com/ubuntu intrepid partner





# emenense messenger download

# deb http://apt.emesene.org/ ./

# deb-src http://apt.emesene.org/ ./



# mac osx look

# deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main

# deb-src http://ppa.launchpad.net/awn-testing/ubuntu intrepid main



deb http://nl.archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse

deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid universe main multiverse restricted #Added by software-properties

deb http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted

deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted

deb http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted

deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted



bas@bas-laptop:~$ 

```

@ Vadi: 
Deselected all the third-party software. 
It works! 

I don't think the above code is needed any more, since the problem seems to be solved for now.

Sorry for the long post.

Thanks for the VERY quick answer!

---

