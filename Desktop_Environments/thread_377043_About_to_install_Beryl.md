---
title: "About to install Beryl"
date: 2007-03-05
forum: Desktop Environments
---

### Post by bluefireball on 2007-03-05
Hey guys
I just finished a fresh install of Edgy and about to install Beryl. I have tried this before but i have totaly messed it up. I have a readeon 9550. Which drivers should i use? XGL or AIGLX?
Thanks for the responses in advance, and if anyone has a link to a well written guide I would appreciate it,

Bluefireball

---

### Post by Waappu on 2007-03-05
Hi

I have used these guides on my ATI 9250 and I think AIGLX is better choise
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI)

You can also try my script
[http://ubuntuforums.org/showthread.php?t=338771](http://ubuntuforums.org/showthread.php?t=338771)

---

### Post by bluefireball on 2007-03-05
Thankyou for the swift reply. A++.

Ha sounds like eBay

---

### Post by Sizzlintrumpet on 2007-03-05
> **Waappu said:**
> Hi

I have used these guides on my ATI 9250 and I think AIGLX is better choise
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI](https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI)

You can also try my script
[http://ubuntuforums.org/showthread.php?t=338771](http://ubuntuforums.org/showthread.php?t=338771)

Hey I'm pretty new to Ubuntu, and I'm impressed by the visual styles that beryl have to offer it, I have a pretty generic Intel 855 graphics card, and was wondering, what commands I have to type in the terminal to get working. I tried to follow the guides on the beryl project's site, but nothing seems to work...please help. 

P.S. I'm running Edgy Eft

---

### Post by ffxr on 2007-03-05
Sizzlintrumpet what does 

```
glxinfo | grep direct 
```

give back..? 

if its **direct rendering: Yes ** you might be in luck.. tho no guarantees'.. 

you can continue with this guide:

[https://help.ubuntu.com/community/BerylOnEdgy?highlight=%28beryl%29#head-793d6ee7eb031a42185b9a87913540d396e3f28f](https://help.ubuntu.com/community/BerylOnEdgy?highlight=%28beryl%29#head-793d6ee7eb031a42185b9a87913540d396e3f28f)

---

### Post by Sizzlintrumpet on 2007-03-05
It is a yes, and I'm going to do a follow through on your guide...thank you, and I'll let you know the results go in a few minutes.

---

### Post by bluefireball on 2007-03-05
> **ffxr said:**
> Sizzlintrumpet what does 

```
glxinfo | grep direct 
```

give back..? 

if its **direct rendering: Yes ** you might be in luck.. tho no guarantees'.. 

you can continue with this guide:

[https://help.ubuntu.com/community/BerylOnEdgy?highlight=%28beryl%29#head-793d6ee7eb031a42185b9a87913540d396e3f28f](https://help.ubuntu.com/community/BerylOnEdgy?highlight=%28beryl%29#head-793d6ee7eb031a42185b9a87913540d396e3f28f)

Crap mine is reporting back that IT DOES SUPPORT it but my car claims it does not support visual 0x4b

---

### Post by Sizzlintrumpet on 2007-03-05
Okay everything is working perfectly, no problems anywhere, thank you so much for the help.

---

### Post by Waappu on 2007-03-06
> **bluefireball said:**
> Crap mine is reporting back that IT DOES SUPPORT it but my car claims it does not support visual 0x4b

Hi

Beryl should still work. You can't use water plugin, but rest should be fine.

---

### Post by harakiri1976 on 2007-03-06
Hello Guys!

I'm using Dapper and I'm having problems with Beryl too!
I'm using an Asus A6JC laptop with a GeForce GO 7300. I followed these two tutorials and Beryl Crashed: (one of them is in Portuguese, sorry)
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX)
[http://www.guiaubuntupt.org/wiki/index.php?title=Xgl_Dapper](http://www.guiaubuntupt.org/wiki/index.php?title=Xgl_Dapper)
I don't know where is the problem. I think I've installed nvidia drivers correctly.

 I made :

 glxinfo | grep direct

and I got this:
 
nuno@ana-laptop:~$ glxinfo | grep direct
direct rendering: Yes

I think everything is ok except 3 missing repositories is my sources.list that didn't work well and there might be the problem. I can't solve it :( I wish somebody could give me some clues.

I get this error everytime I do updates:
[http://www.media.blutkind.org/xgl/dists/dapper/Release.gpg:](http://www.media.blutkind.org/xgl/dists/dapper/Release.gpg:) Could not resolve 'www.media.blutkind.org'
[http://www.media.blutkind.org/xgl/dists/dapper/main/binary-i386/Packages.gz:](http://www.media.blutkind.org/xgl/dists/dapper/main/binary-i386/Packages.gz:) Could not resolve 'www.media.blutkind.org'
[http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz:](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz:) 301 Moved Permanently

..and this is my sources.list:

 
deb-src [http://neacm.fe.up.pt/ubuntu/](http://neacm.fe.up.pt/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
#AUTOMATIX REPOS END

#BERYL
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://www.media.blutkind.org/xgl/](http://www.media.blutkind.org/xgl/) dapper main
#Beryl REPOS END

#EasyCam2
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
#EasyCam2 END
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./


If you guys detect any errors please help me telling me them.
Thank You!

---

### Post by jhenager on 2007-03-06
For one thing, I can't connect to [http://www.media.blutkind.org](http://www.media.blutkind.org), so that makes me wonder right there.

---

### Post by harakiri1976 on 2007-03-06
Yes, I hear you. 
Should I follow Edgy instructions and change sources.list from Edgy to Dapper?...(???)

---

