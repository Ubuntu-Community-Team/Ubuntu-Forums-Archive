---
title: "Trying to Install Tint2 Taskbar Help Please"
date: 2015-09-06
forum: Desktop Environments
---

### Post by logan012 on 2015-09-06
Today I finally managed to install Ubuntu 14,04.3 to a 32gb flash drive so that I could give it a try out. Only been using it about an hour and I really like what I see. I have several questions/comments but now I'll submit this:

I'm attempting to install the Task2 taskbar

When entered and I hit return I get the following message: **E: Unable to locate package tint2**

Is this because I'm currently gutless and have installed only to a flash drive or ......?

Thank you

---

### Post by vasa1 on 2015-09-06
> **logan012 said:**
> ...
**_When entered_** and I hit return I get the following message: **E: Unable to locate package tint2**

Is this because I'm currently gutless and have installed only to a flash drive or ......?

Thank you
No. But do share what you "entered".
```
06:46 AM ~ $ apt-cache policy tint2
tint2:
  Installed: 0.11+svn20121014-1
  Candidate: 0.11+svn20121014-1
  Version table:
 *** 0.11+svn20121014-1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
07:05 AM ~ $ 

```

---

### Post by logan012 on 2015-09-06
ubuntu@ubuntu:~$ sudo apt-get install tint2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package tint2

---

### Post by CantankRus on 2015-09-06
Enable the universe repository.
Using the terminal....
```
software-properties-gtk
```
and mark as in pic.

---

### Post by vasa1 on 2015-09-06
Have you enabled the "universe" repository? *tint2* is in *universe*:

```
09:11 AM ~ $ apt-cache show tint2
Package: tint2
Priority: optional
Section: **_universe_**/x11
Installed-Size: 380
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Sebastian Reichel <sre@debian.org>
...
```

---

### Post by logan012 on 2015-09-07
New problem. After posting what I had entered in Terminal, I took a break and closed the lid on my laptop. Unlike a few times before while using Ubuntu, I lost my wifi. In networking it says "out of range". I'm within 5 ft. of the modem. The only way I know to go to Windows is to click "shutdown" in the upper right corner, therefore, I did that. I powered up my laptop, it goes to Windows and I have wifi. I have done this 3 times now. I'm sending this through another laptop using Windows. I can try yall's recommendations if it doesn't require the internet. If it does require the internet, I guess I'm sol until I can get that figured out. I do greatly appreciate your help though. For whatever reason after numerous attempts, I now have connectivity.

---

### Post by logan012 on 2015-09-07
I have me a taskbar. Thank you guys very, very much. I tried the info from vasa1 in the Terminal and it required me to do it from/as "root". The instructions from CantankRus worked. The only issue I had was I was required to logout and back in for the bar to appear. It wouldn't recognize my usrid/password after numerous attempts. I shutdown, logged back into Windows just to make sure my login was good. It was. I booted to usb and had me a little taskbar. I'm a very tired and happy camper. In life, I'm pretty cautious about somethings and stupid wide open on others. As you have likely noticed, my computers skills are lacking but I get by. My intro to computers came via Unix and some really high end Silicon Graphics sparc stations. A few years later we non-technical types (this was at work) were given desktops tied into a network. The point being is I can't in good conscience be a Windows basher.  It served me very well for the past several years.Now Apple, that's a different story, I still have an iphone, bought a  new iPad a couple of years ago and GAVE it away after about one month.  Not that I have a problem w/ ios but I have a huge problem with them  having absolute control over me, the user/customer. To me it's like a  "mother may I" deal. I have had folks through different forums recommend Linux for years and I just didn't heed their call. My ignorance, no excuses except for that cautious side of me. I fairly sure as it stands right now I'll likely be installing Linux on this computer. There's just so much to choose from and I'm totally lost. The past few days I've been seeing praises of whatever Plasma 5 is. Being totally ignorant of all these choices, it's difficult to recognize bs hype and true evaluations. Anyhow, thanks guys.:D

---

