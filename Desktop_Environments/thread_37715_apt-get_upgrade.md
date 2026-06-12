---
title: "apt-get upgrade"
date: 2005-05-28
forum: Desktop Environments
---

### Post by Frozen on 2005-05-28
hey guys

i was just wondering if its safe to do a apt-get upgrade on kubuntu yet, i did 1 a week ago or so and kde messed up, not hugly but enuf 4 me 2 find it easier to re-install kubuntu rather than sort it out. im new to kubuntu so am not sure where to find latest info on fixed packages n stuff. i did read sumwhere than the problem was caused by a package in the apt-get upgrade, cant remember which 1 tho, cld habe bin kdelibs or sumthin

hope u can help

regards

frozen

---

### Post by bored2k on 2005-05-28
[QUOTE=Frozen]hey guys

i was just wondering if its safe to do a apt-get upgrade on kubuntu yet, i did 1 a week ago or so and kde messed up, not hugly but enuf 4 me 2 find it easier to re-install kubuntu rather than sort it out. im new to kubuntu so am not sure where to find latest info on fixed packages n stuff. i did read sumwhere than the problem was caused by a package in the apt-get upgrade, cant remember which 1 tho, cld habe bin kdelibs or sumthin

hope u can help

regards

frozen[/QUOTE]
 It should be reliable. apt-get upgrade should make no harm on your machina. dist-upgrade is more complete, but the current state should be ok. That was probably caused by some shady repositories in your sources.list

---

### Post by Kamping_Kaiser on 2005-05-28
As far as i know, as long as you are running Kubuntu-Hoary, you are ok. If you try and upgrade to Breezy, you *will* have problems. im in debian now because i cant get ubuntu ticking right ;).

---

### Post by jagguars on 2005-05-28
i'm quite a noob to, but what i found out (till yesterday) ;) the only important thing at upgrades or installations is to set the right servers in the sources.list . you find this file in the /etc/apt  . look at this file and mark all instable or testing pakage servers with a # before. it will make apt-get and all other installing programs not to use this servers.
done that you should upgrade like hell and no error should occure. :D

---

### Post by Xian on 2005-05-28
[QUOTE=Frozen]i did read sumwhere than the problem was caused by a package in the apt-get upgrade, cant remember which 1 tho, cld habe bin kdelibs or sumthin[/QUOTE]
There was a problem with the kdelibs package recently: [Failed Update](http://www.ubuntuforums.org/showthread.php?t=28678&highlight=kdelibs), [Apt-Get Issue](http://ubuntuforums.org/showthread.php?t=28721)

---

### Post by Frozen on 2005-05-28
hey, thanks for the quick replys. it was the errors that Xian mentioned that i was reffering to. was just wondering if i do another upgrade wether ill get the same problem. i had updated my sources.list with help from ubuntuguide.org and i have now added sources from the kubuntu guide that i found on the kubuntu home page. its prolly down to me not knowing much about debian, have only used RPM based distro's before ubuntu and kubuntu.

ta for the advise, tiz greatly appreciated

Regards

Frozen

---

### Post by fdoving on 2005-05-28
[QUOTE=Xian]There was a problem with the kdelibs package recently: [Failed Update](http://www.ubuntuforums.org/showthread.php?t=28678&highlight=kdelibs), [Apt-Get Issue](http://ubuntuforums.org/showthread.php?t=28721)[/QUOTE]
 This issue has been fixed. Updated packages are in the hoary-updates section.
Make sure hoary-updates is enabled. Guide: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

- Frode

---

### Post by Frozen on 2005-05-28
cheers 4 that. i just did an upgrade and alls ok. cheers. 

just out of inserest what does apt-get dist-upgrade do?

ta

Frozen

---

### Post by Xian on 2005-05-28
[QUOTE=Frozen]just out of inserest what does apt-get dist-upgrade do?[/QUOTE]
It upgrades all the applicable packages on your system, including those that would require new (uninstalled) dependencies in order to function.

---

