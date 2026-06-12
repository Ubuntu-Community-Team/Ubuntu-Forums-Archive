---
title: "Yum installer package"
date: 2008-01-09
forum: Fedora/RedHat and derivatives
---

### Post by fedex1993 on 2008-01-09
Okay i am downloading openbox and some other file adn when i usually download on ubuntu there like 1 2 3 done well with yum it taking me about 30-an hour to download and isntall and it is starting to piss me off could it be because of a slow mirror or my internet connection ro what?

---

### Post by SunnyRabbiera on 2008-01-09
yum is notorious for this, thus why I hate it.
its why I stuck to apt based distro's, plus fedora's mirrors blow.
If you prefer rpm I would suggest mandriva 2008 instead, urpmi has come a long way.

---

### Post by RebounD11 on 2008-01-09
Try Yumex or Synaptic in Fedora... work faster than Yum... and don't crash.

Turn of the updates service that runs in the background by default (I did permanently) because it takes up bandwidth.

And someone explain to me why does Fedora 8 log me out when I try to play Counter-Strike... (other games work... only not with Cedega or Wine) :|

---

### Post by fedex1993 on 2008-01-09
thanks but i decied to build a ubuntu system starting with a command line and going from there :)

---

### Post by igknighted on 2008-01-10
Install the packages 'yum-presto' and 'yum-fastestmirror'.  Fastestmirror (as you might expect) selects the fastest mirror available to you.  Presto uses delta-rpms where available (so you don't have to download the entire new version of something for a tiny patch).  Using these plugins, Yum is as fast, if not faster than apt.

Sunny, I think your info on Yum is quite outdated.  Yes, it has had issues in the past (as all package managers have), it just happens to have been around forever so people remember the early days when it was really bad.  For the past year+ yum has been an excellent option, on par with Urpmi and Apt in speed, and quite a bit more powerful.

---

### Post by SunnyRabbiera on 2008-01-10
> **igknighted said:**
> Install the packages 'yum-presto' and 'yum-fastestmirror'.  Fastestmirror (as you might expect) selects the fastest mirror available to you.  Presto uses delta-rpms where available (so you don't have to download the entire new version of something for a tiny patch).  Using these plugins, Yum is as fast, if not faster than apt.

Sunny, I think your info on Yum is quite outdated.  Yes, it has had issues in the past (as all package managers have), it just happens to have been around forever so people remember the early days when it was really bad.  For the past year+ yum has been an excellent option, on par with Urpmi and Apt in speed, and quite a bit more powerful.

not in my experience, YUM is miserable in my opinion compared to apt and urpmi

---

