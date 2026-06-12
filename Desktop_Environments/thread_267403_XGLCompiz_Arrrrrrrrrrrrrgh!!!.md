---
title: "XGL/Compiz Arrrrrrrrrrrrrgh!!!"
date: 2006-09-28
forum: Desktop Environments
---

### Post by obe1kenobi on 2006-09-28
I apologize in advance for sounding really irritable, but this is ticking me off.  ](*,) 

I tried installing it according to [http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267) this forum.  It worked but wouldn't start with Ubuntu. I noticed there was a link to newer instructions on top and used those no luck.  I've tried three or four other sets of instruction and no luck. Many of them ask to install csm, cgwd, and cgwd-themes which don't exist according to my computer.  I've added any repository they've asked for and no luck.  ](*,)  Xgl was great when I had for that little while, and now I'm just frustrated. :x

I have tried a couple clean installs, so I don't know what's wrong.

(Nvidia card)

P.S. It would nice to have a stickied, or HOW-TO thread with instructions on Xgl/Compiz for Dapper that could be kept updated with the new instructions.  (assuming there isn't one already that I've been missing)

Any help would be great. Thanks.:x

---

### Post by Lord Illidan on 2006-09-28
Did you run sudo apt-get update after increasing the repos?

---

### Post by eljaco on 2006-09-28
Hey, I need some help too. I think it might be we don't have the right repos for csm.

This is my /etc/apt/sources.lst

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

I am now having the really annoying problem that the GUI does not paint everything (mainly text - images seem to be working fine.) I was wondering if there was a way to erase all this XGL stuff and then restart from scratch.

Thanks.

---

### Post by Tuxman on 2006-09-28
Could it have something with this to do?
[http://forum.beryl-project.org/topic-4591-beryl-informations-announcement](http://forum.beryl-project.org/topic-4591-beryl-informations-announcement)

---

### Post by obe1kenobi on 2006-09-28
I did do a sudo apt-get update.

And the Beryl thing might be the problem, but I was hoping one of you knew for sure.

Thanks

---

### Post by invisibastard on 2006-09-28
I went through the same nightmare, then found an XGL/Compiz install page (somewhere, lost the link) that warns that the repo's are broken now and says do not attempt to install. I have read in other forums that Beryl should be ready in a week. It is frustrating that this warning isn't posted anywhere. I am trapped mid-install, with no idea how to fix, what is installed and what isn't... blah blah blah. Luckily I was able to get X started again, my computer went down during a power outage, I planned to leave it on until Beryl was running. 

I should have taken notes during the install, it was only after it failed that I found out XGL/Compiz was uninstallable. 

Good Luck,
Rich

---

### Post by obe1kenobi on 2006-09-28
Thanks a lot. :D I agree that they should mention that somewhere that their repos are broken. :x

Hopefully they get Beryl up and running soon.  

Thanks again.

---

