---
title: "Cedega 5.01 install troubles."
date: 2006-01-20
forum: Gaming &amp; Leisure
---

### Post by Dark Damo on 2006-01-20
I get this when trying to install

> damo@OMG:~$ sudo dpkg --install /home/damo/Desktop/cedega-5.0.1_DEB_[PtitGNU]/cedega_5.0.1_i386.deb
(Reading database ... 114568 files and directories currently installed.)
Preparing to replace cedega 5.0.1 (using .../cedega_5.0.1_i386.deb) ...
Unpacking replacement cedega ...
dpkg: dependency problems prevent configuration of cedega:
 cedega depends on xlibs (>> 4.1.0); however:
  Package xlibs is not installed.
dpkg: error processing cedega (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cedega
damo@OMG:~$


Anyone help pleeeeaaasssee?

---

### Post by happyponcho42 on 2006-01-20
> sudo apt-get install xlibs

After searching for the name of your cedega file, I'm lead to believe that you didn't purchase Cedega for it's precompiled packages, but rather downloaded it from a torrent?  $5.00/month isn't much and it includes support from TransGaming.

---

### Post by Dark Damo on 2006-01-20
Thanks but i get an error

> damo@OMG:~$ sudo apt-get install xlibs
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  k3b: Depends: kdelibs4 (>= 4:3.1.2) but it is not installable
       Depends: libarts1 (>= 1.1.2) but it is not installable
       Depends: libqt3c102-mt (>= 3:3.1.1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
damo@OMG:~$






Duh im not paying for some shitty software. $9 a month for me because i am Aussie. And i dont have a credit card because i am 14. And i'm not allowed to buy stuff over the internet. Maybe if it was a one time pament and was released in a store i would consider buying it. 


Will you apply to get me a credit card please?

I dont think so.

---

### Post by happyponcho42 on 2006-01-20
You consider it shitty software, yet you're so persistent in getting it to install.  Do you really think this 'shitty software' that took time to develop is worth all your troubles then?

Have you tried the 'apt-get -f install' they suggest?

---

### Post by Dark Damo on 2006-01-20
Problem solved. Thanks for help

---

### Post by xBIGx on 2006-09-13
Dark Damo plase explain i'm a noob user with the same problem..Thanx

---

### Post by Perfect Storm on 2006-09-14
Newer cedega .deb packages doesn't have this problem. 


Don't use pirated software!!! Piracy is illegal!

Thread closed.

---

