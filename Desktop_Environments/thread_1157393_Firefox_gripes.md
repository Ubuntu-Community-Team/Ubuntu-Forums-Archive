---
title: "Firefox gripes"
date: 2009-05-12
forum: Desktop Environments
---

### Post by systemgod on 2009-05-12
Hi,

I'm a long time linux user (and sysadmin).  After I got married a few years ago I kind of forced my why wife to use Linux too.  This all went well for a few years however since a few months (not sure when it started) I'm experiencing serious problems with firefox.  At least once every week firefox will refuse to start claiming another instance is already running (which of course is not the case). I then manually need to remove the lock files and even the places.sqlite* files otherwise firefox will have lost its bookmarks. Note that this happens even when I'm 100% sure I exited firefox properly.  Since the last few weeks when I use Gmail I suddenly get #102 errors which I can only resolve by removing the .mozilla directory completely and creating a new profile.  For me this is a serious nuisance, however for my non-computer-savvy wife this is making it impossible to do anything useful on linux (she only uses firefox and openoffice anyway). It is getting extremely hard for me to justify to keep on asking her to work on linux.

Has anybody else seen an increase in this kind of problems? If it was just my account I would blame it on firefox plugins (but I'm only using 2 or 3), but my wife does not use any plugins at all.

Is there another full-featured browser on Ubuntu that I can use? (I tried using konqueror but it doesn't even come close to firefox in terms of javascript (=read: any modern website) support) 

I'm using Ubuntu 8.10 AMD64, fully patched.

Thanks in advance,

Nico

---

### Post by nacho32 on 2009-05-12
i would suggest in a remove and reinstall , and Opera is a pretty sweet browser to, and go for the 9.04 it is a great OS.:) running the 64 bit stable and sweet:)

---

### Post by sir_nasty on 2009-05-12
with a couple of the firefox releases I had major issues on both my mac and xp, none with clean ubuntu 8.1 hardy....  I'd suggest seeing if their is an updated version or doing a purge/re-install... I like the current version but a few of them just flat worked like garbage....

---

### Post by sir_nasty on 2009-05-12
another side note.... not sure how it would work on a desktop pc but the 9.04 netbook remix has a very friendly interface....

---

### Post by systemgod on 2009-05-12
I just realized Opera is still out there after I posted the message. Am downloading it know.

I will definitely try reinstalling firefox (why didn't I think of that!) when I get home (I'm currently on a business trip and got an angry phone call from my wife about firefox).

Unfortunately Ubuntu 9.04 is not really an option for me as I have an ATI card which is apparently not supported by ATI anymore (and I really want the 3D drivers)

Thanks for your very quick reply

Nico

---

### Post by keithld on 2009-05-12
Your defualt Profile could be corrupted... I'd try creating a new one and see if it also acts up...

in a terminal: firefox -profilemanager

---

### Post by systemgod on 2009-05-13
> **keithld said:**
> Your defualt Profile could be corrupted... I'd try creating a new one and see if it also acts up...

in a terminal: firefox -profilemanager
I removed my .mozilla/ directory a number of times (every time I start getting the 102 error as that seems to be the only way to fix it).  The profile is stored in there so I get a new one automaticaly.

Nico

---

