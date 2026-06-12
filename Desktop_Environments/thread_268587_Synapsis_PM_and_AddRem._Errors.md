---
title: "Synapsis PM and Add/Rem. Errors"
date: 2006-09-30
forum: Desktop Environments
---

### Post by OptimusPrime on 2006-09-30
I don't know what I did to do this, but whenever I try to open Add/Remove, I get this:

Failed to check for installed and available applications
This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

And synapsis package manager:

The following problems were found on your system:
E: Type 'http://uk.archive.ubuntu.com/ubuntu/' is not known on line 35 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

What's happening?  Doesn't Ubuntu want me to get more software?

---

### Post by djRobbieF on 2006-09-30
Have you edited your sources.list file?  It's found in /etc/apt

Post it here.

PS - Don't worry; this is easy to fix.

---

### Post by OptimusPrime on 2006-09-30
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by OptimusPrime on 2006-09-30
The sources.list file is empty.  That one is the sources.list_backup

---

### Post by djRobbieF on 2006-09-30
Strange... [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) isn't even in your sources.list file...

Anyone with ideas?

---

### Post by Kateikyoushi on 2006-09-30
Then rename the backup file to sources.list

---

### Post by djRobbieF on 2006-09-30
> **OptimusPrime said:**
> The sources.list file is empty.  That one is the sources.list_backup

Oh gosh, well there you have it.

Copy sources.list_backup to sources.list and do a sudo apt-get update

---

### Post by OptimusPrime on 2006-09-30
Sorry, the sources.list "folder" is empty.  The sources.list file is:

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


deb [http://ftp.debian.org](http://ftp.debian.org) sarg main

[http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

---

### Post by OptimusPrime on 2006-09-30
> **djRobbieF said:**
> Oh gosh, well there you have it.

Copy sources.list_backup to sources.list and do a sudo apt-get update

Well darn it all.  I get this when I try that: You do not have permissions to write to this folder.
Keep in mind, I AM THE ADMIN!

---

### Post by djRobbieF on 2006-09-30
```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```

---

### Post by OptimusPrime on 2006-09-30
You are all gods among men.  Thank you!

---

### Post by djRobbieF on 2006-09-30
np

---

