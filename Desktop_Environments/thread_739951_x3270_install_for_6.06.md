---
title: "x3270 install for 6.06"
date: 2008-03-30
forum: Desktop Environments
---

### Post by stans on 2008-03-30
I'm interested in installing x3270 but all the threads I have found are a bit old. Does anyone have current information about how-to ? 

Thank you

---

### Post by kerry_s on 2008-03-30
it's in the repo's

sudo apt-get update
sudo apt-get install x3270

[http://x3270.bgp.nu/documentation.html](http://x3270.bgp.nu/documentation.html)

---

### Post by stans on 2008-03-30
Thank you very much... but looks like I need to add to my list of repositories ?

E: Couldn't find package x3270

---

### Post by kerry_s on 2008-03-30
open synaptic in your menu, click settings> repositories, make sure there all on, click reload. then just high light any line and start typing x3270 it should go right to it, mark it for install.

---

### Post by stans on 2008-03-30
This is going to be another one of those 'journeys'... no x3270 shows up in my list, and all repositories are checked 'on'.

Thanks again for working with me.

---

### Post by kerry_s on 2008-03-30
i guess 6.06 is just to old to have it.
why are you using 6.06 anyways?

---

### Post by stans on 2008-03-30
Old ? I thought it was the long-term solution. I just upgraded to it not all that long ago. 

I'm what you'd call a casual enthusiast - and don't work in this environment as much as I should. I'm a mainframe programmer by day and try to wind down when at home.

Guess I must have missed something here ?

---

### Post by kerry_s on 2008-03-30
ubuntu is a snap shot distro, long term support only means you will get security fixes, but you won't get any programs that have been added to the repo's since then or any program updates other than security fixes.

i recommend you go with a rolling release, such as debian, you only need to install it once and you just update normally, you can add the repo for lenny if you want more up to date stuff. there's no cut off point, it can always be updated to the latest, just doing the usual updates.
net installer-> [http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

i run debian etch/lenny custom install.

---

### Post by stans on 2008-03-30
I started with Ubuntu several years ago... an in the meantime for this recent upgrade have installed a LOT of applications. Those will all have to be reinstalled, eh ?

---

### Post by kerry_s on 2008-03-30
yeah, but there probably all old.

hold off a bit, let me think if there's a easier way for you to get that.

---

### Post by stans on 2008-03-30
I could download the x3270 source and compile it. Should learn how to do that.

---

### Post by kerry_s on 2008-03-30
here, try the deb->
[http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/i/ibm-3270/x3270_3.3.4p6-3.3_i386.deb](http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/i/ibm-3270/x3270_3.3.4p6-3.3_i386.deb)

sudo dpkg -i *.deb
or 
just click on it(can't remember if dapper had gdebi to do installs)


if something go's wrong.
sudo apt-get -f install

you might also need->
[http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/i/ibm-3270/xfonts-x3270-misc_3.3.4p6-3.3_all.deb](http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/i/ibm-3270/xfonts-x3270-misc_3.3.4p6-3.3_all.deb)
[http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/i/ibm-3270/3270-common_3.3.4p6-3.3_i386.deb](http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/i/ibm-3270/3270-common_3.3.4p6-3.3_i386.deb)
[http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/i/ibm-3270/pr3287_3.3.4p6-3.3_i386.deb](http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/i/ibm-3270/pr3287_3.3.4p6-3.3_i386.deb)

---

### Post by stans on 2008-03-30
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

---

### Post by kerry_s on 2008-03-30
> **stans said:**
> dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

make sure your in the same place you downloaded to.
put them all in the same place.
type> ls <to see whats there
type> cd <to change directories, example: cd Desktop 

do the top 1 again i changed it to the 3.3 version to match all the other dependency's.

put all 4 in the same place and run the command.

---

### Post by stans on 2008-03-30
Thanks again for assisting. Looks like my libc6 is out dated... oh well... the adventure continues.

---

### Post by stans on 2008-03-30
The following packages have unmet dependencies:
  3270-common: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed
  pr3287: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed
          Depends: libssl0.9.8 (>= 0.9.8c-1) but 0.9.8a-7ubuntu0.5 is installed
  x3270: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed
         Depends: libssl0.9.8 (>= 0.9.8c-1) but 0.9.8a-7ubuntu0.5 is installed
E: Unmet dependencies. Try using -f.

I've made an attempt - but cannot figure this out.

How can I upgrade the two items mentioned above ?

---

### Post by kerry_s on 2008-03-30
let me look for a older version of x3270.
i get back to you.

i'm sorry man i can't find a dapper version for x3270 + it's dependency's.

i did come across some posts which says it was in the dapper repo.
can you post your /etc/apt/sources.list so i can see if your missing repo's.

**gedit /etc/apt/sources.list**

---

### Post by stans on 2008-03-30
I'm very seriously considering doing it the 'old fashioned way' - compile the source.

I do appreciate your help.
-----------------------------------------------------------------------------------------------

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
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
#AUTOMATIX REPOS END
deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib
deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib/

---

### Post by kerry_s on 2008-03-30
well your sources.list looks fine as far as i can tell.

if you want to try compiling it go for it, i'm all out of ideas.

if all else fails, like i said go debian, you will never have these kind of problems.

wait i have 1 more idea, try using the debian repo, i think dapper was still close enough to debian it might work, just grab what you need then disable the repo.

**sudo gedit /etc/apt/sources.list**
add
**deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) etch main contrib non-free**

[B]sudo apt-get update
sudo apt-get install x3270
[/B]
then remove the repo or #(comment) it out.

good luck to you.

---

### Post by stans on 2008-03-30
Seems to always be a battle when one wants to get something done... sometimes it gets very old, you know ?
-----------------------------------------------------------------------------------------------------------------------

Get:19 [http://ftp.us.debian.org](http://ftp.us.debian.org) etch/non-free/ Packages [83.8kB]
Fetched 4488kB in 25s (179kB/s)
Reading package lists... Error!
W: GPG error: [http://ftp.us.debian.org](http://ftp.us.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
E: Dynamic MMap ran out of room
E: Error occurred while processing scite (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.us.debian.org_debian_dists_etch_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by kerry_s on 2008-03-30
what is that scite error? looks like a incomplete install.
ya need to fix that first.

comment(#) out the debian repo.
run> **sudo apt-get -f install**
before you proceed.

okay you got to many repos active turn some of the other ones off, just put a # in front of them.  and uncomment the debian repo.

then try this->
[B]sudo apt-get clean
sudo apt-get update
sudo apt-get install x3270[/B]

don't worry about the gpg key error, that's nothing, your only temperately using the repo.

hang in there, those errors are minor.

---

### Post by stans on 2008-03-31
Package x3270 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package x3270 has no installation candidate

---

### Post by kerry_s on 2008-03-31
did you run> sudo apt-get update <first ?

here's what it say on mine->

---

### Post by stans on 2008-03-31
Yes, I ran the apt-get's as you showed. 

I've decided to consider loading Debian on this box... but will do some homework first to see if it will be worth the effort.

I don't even have a mainframe host that I can access (with this machine) so there is no real urgency to get x3270 installed.

Thanks again for all your efforts to assist me.

---

### Post by kerry_s on 2008-03-31
okay.

yes, debian is much better. especially when you want it to just work.
i do a custom install with only what i want, my machines only 450mhz 256mb ram.

---

