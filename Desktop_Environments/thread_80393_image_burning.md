---
title: "image burning"
date: 2005-10-22
forum: Desktop Environments
---

### Post by bmarilena on 2005-10-22
Hi!

I have a problem in burning an immage on a cd under ubuntu 5.10.

Any ideea about how to do this?

Thanks.

Marilena

---

### Post by bionnaki on 2005-10-22
what problems are you having?

---

### Post by bmarilena on 2005-10-22
well I have downloaded the 5.10 f
with torent, and try to burn it on a cd.

I did, but is not booting, soa is just a data folder there.
How can I burn this immage on cd and start install using this cd in the regular way?

---

### Post by migueljacq on 2005-10-22
Download Gnomebaker

sudo apt-get install gnomebaker

Click on 'Burn CD Image'

bingo

---

### Post by bmarilena on 2005-10-22
ok, tryed, bur... tyhe answer is [I]Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnomebaker[/I]

What should I do next?

---

### Post by migueljacq on 2005-10-22
hmmm... post the contents of your /etc/apt/sources.list file?

---

### Post by bmarilena on 2005-10-22
ok, here it is:
[I]#deb file:///cdrom/ breezy main restricted

deb [ftp://ro.archive.ubuntu.com/ubuntu/](ftp://ro.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [ftp://ro.archive.ubuntu.com/ubuntu/](ftp://ro.archive.ubuntu.com/ubuntu/) breezy main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) breezy universe
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
[/I]

---

### Post by migueljacq on 2005-10-22
Ok go here

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

and follow the instructions for Breezy 5.10

then try again

---

### Post by bmarilena on 2005-10-22
ok, tried.... but got stuck on updating... I got this message:
[I]Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/I]
What should i do next?

---

### Post by bmarilena on 2005-10-22
tried again and I got this: 
[I]Fetched 191B in 4s (42B/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems[/I]
Right now I'm installing the updates.

---

### Post by migueljacq on 2005-10-22
Hmm I've seen that pop up several times for some users. Usually it's either of two things:

1) Wrong repositories (we know you have the right ones because you just replaced your sources.list)

2) Some sort of external repository server error - nothing you can do but keep trying 

:( sorry

also: check [www.ubuntuguide.org](www.ubuntuguide.org)

there's a section in there for burning ISO images - it might also work and save all this hassle - but at least your repositories are correct, will save you from future problems

---

### Post by bmarilena on 2005-10-22
seems I managed to install gnomebaker... how do I burn immage using it?

---

### Post by migueljacq on 2005-10-22
Go to Applications >> Sound & Video >> Gnomebaker

Click the button that says 'Burn CD Image'

Choose the image file.

---

### Post by bmarilena on 2005-10-22
thanks a lot... seems is working
Keep the fingers crossed for me :))
Hope to install again Breezy. 

Thanks again!

---

