---
title: "apt-get problems"
date: 2005-05-28
forum: Desktop Environments
---

### Post by VyRuZ on 2005-05-28
I recently installed Kubuntu on my internet pc and wanted to burn a CD with some music.... Started K3B and it said it needed cdrdao to actually burn CD's ...
Switched to root and started the Konsole , typed apt-get install cdrdao but it didn't work , giving me an error about packages 

Anyone help me ... I'll post the error in 3 minutes when i switch to root , as i need some time to finish something in this account

EDiT : Package cdrdao is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cdrdao has no installation candidate

Ok i thought this might be beacuse there is no cdrdao package , but mozilla-firefox gives the same error

Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate

What could be the problem ?? I installed the same version of Kubuntu that i have to a frined and it works there ...

---

### Post by GeneralZod on 2005-05-28
Something is missing from your /etc/apt/sources.list 

Please post the contents of that file here, and we'll take a look :)

Alternatively, check out [this](http://ubuntuguide.org/#repositories) part of the Ubuntu Starters Guide.

Hope his helps,
Simon

---

### Post by VyRuZ on 2005-05-28
First of all , thanks for replying and trying to help a poor newbie ;)
Second , here's the file

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

Should i edit it with what that guide says , and then try again ??

EDiT - Works ! Thanks man ! 

I am wondering why didn't the OS change that file ... It should have change it , right ??

---

### Post by GeneralZod on 2005-05-28
[QUOTE=VyRuZ]EDiT - Works ! Thanks man ! 

I am wondering why didn't the OS change that file ... It should have change it , right ??[/QUOTE]

Glad to hear it :) I can't actually remember whether the file is supposed to be automatically changed, but I've seen at least one guy with the same problem, so I guess not :) Flick through the guide some more, as it is well worth it, and have fun with your new Kubuntu!

---

### Post by Firetech on 2005-05-28
> **VyRuZ]First of all , thanks for replying and trying to help a poor newbie  said:**
> / hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://ro.archive.ubuntu.com/ubuntu](http://ro.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

Should i edit it with what that guide says , and then try again ??

EDiT - Works ! Thanks man ! 

I am wondering why didn't the OS change that file ... It should have change it , right ??
 hmm you have everything commented out, did you have internet when you installed?
try removing all the #'s in front of the lines with only one (1) #. (all of them are starting with deb or deb-src after the #)

---

### Post by VyRuZ on 2005-05-28
Will have a LOT of fun mate !!
Love the fact that with Linux i forgot the color of my CPU-Usage led :)

---

