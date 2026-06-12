---
title: "kget - installation trouble- kde 3.5 repo missing/down?"
date: 2005-12-19
forum: Desktop Environments
---

### Post by Beej on 2005-12-19
I'm running Kubuntu Breezy with KDE 3.5. When I run sudo apt-get install kget from the terminal i get the following error


Err [http://kubuntu.org](http://kubuntu.org) breezy/main kget 4:3.5.0-0ubuntu0breezy1
  404 Not Found
Failed to fetch [http://kubuntu.org/packages/kde35rc2/pool-breezy/kdenetwork/kget_3.5.0-0ubuntu0breezy1_i386.deb](http://kubuntu.org/packages/kde35rc2/pool-breezy/kdenetwork/kget_3.5.0-0ubuntu0breezy1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I've put the web address into konqueror and found that thekdenetwork folder does not seem to contain anything.

Have the kde 3.5 repos been moved or gone down? I've been trying this for a few days now.

Thanks,

Beej.

---

### Post by jetpeach on 2005-12-19
I'm having the same problem, I added www. in front of the names and some started working.

---

### Post by Beej on 2005-12-19
Okay adding www. infront of the repo didn't work. Here is my sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse 

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse 

## PLF 
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

#  koffice 1.4.2 ([http://www.kubuntu.org/announcements/koffice-142.php](http://www.kubuntu.org/announcements/koffice-142.php))
deb [http://kubuntu.org/packages/koffice142](http://kubuntu.org/packages/koffice142) breezy main

deb [http://kubuntu.org/packages/kde35rc2](http://kubuntu.org/packages/kde35rc2) breezy main
deb [http://kubuntu.org/packages/amarok-1.3.7](http://kubuntu.org/packages/amarok-1.3.7) breezy main

Anybody any ideas?

---

### Post by Rackerz on 2005-12-19
It's not related to the specific subject but, Beej, is your ## PLF source the Penguin Liberation Front? Also is there much difference in Koffice then in Openoffice.

Thanks

---

### Post by Beej on 2005-12-20
You know what? I'm not sure, I didn't use them myself. I switched to kubuntu from ubuntu recently, and I decided rather than install all the bits and bats manually, I would use easy kubuntu. I think this must have added the koffice repo.

Beej.

---

### Post by Beej on 2005-12-21
bump

---

### Post by manubreizh on 2005-12-21
hi,
have you seen this :
[http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)
now there's repo for final kde 3.5 in kubuntu ; you sources.list shows rc2, it may be not assumed by the server (or the server was down at this moment ?)
in my case, the repo for 3.5 final works like a charm !
for rackerz : plf is th epenguin liberation front (as i know) ; and there is no such differences between koffice and openoffice, almost export in pdf and navigation that seem not to be in koffice (but i don't use it , i've only tried once or twice, so experienced users may think i'm wrong and i appologise for this in advance :) !)

---

### Post by Beej on 2005-12-21
Thanks manubreizh, this sorted my problem out.

---

