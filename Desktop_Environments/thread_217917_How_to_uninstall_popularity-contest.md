---
title: "How to uninstall popularity-contest?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by Hop-Frog on 2006-07-17
I stumbled upon a spyware package called popularity-contest, installed on my system.  I'm not sure how it got there, but I want to remove it.

I tried to uninstall it, but it said that it would also have to uninstall ubuntu-base and ubuntu-standard.   Are these two packages important?  Are they needed for receiving software updates?  Or are they only needed for huge updates, for instance going from Dapper Drake to Edgy Eft?

---

### Post by T700 on 2006-07-17
Where exactly (URL?) did you get this program?  How did you install it (apt-get, aptitude, Adept, etc.)?  *What makes you believe it is spyware?*

Paul

---

### Post by aysiu on 2006-07-17
It reports anonymously what packages you install and for which architectures. It comes installed, but I don't believe it comes *turned on*.

It's an opt-in policy, as far as I know. To be sure, paste this command into the terminal: ```
cat /etc/popularity-contest.conf
``` If all is well, it should look something like this: ```
# Config file for Debian's popularity-contest package.
#
# To change this file, use:
#        dpkg-reconfigure popularity-contest
#
# You can also edit it by hand, if you so choose.
#
# See /usr/share/popularity-contest/default.conf for more info
# on the options.

MY_HOSTID="cd8530da83df484a871b56cc2bae683a"
**PARTICIPATE="no"**
USEHTTP="yes"
``` If all is not well, it should say ```
PARTICIPATE="yes"
``` I'm pretty sure that in order to activate participation, you have to do ```
sudo dpkg-reconfigure popularity-contest
``` **Edit**: I just looked at my other Ubuntu computer, and it appears to default to a "no" on participation.

---

### Post by gruffy-06 on 2006-10-26
The "popularity-contest" package is NOT spyware! Even though it may anonymously report to Ubuntu package usage data, NO personal data is ever given away. This data helps the developers decide what to put in main, universe, on the install cd, etc.

I do understand that users who do not want this package installed do not want to help make Ubuntu better for other people. Nevertheless, just remove the *popularity-contest* package. *Ubuntu-base* and *ubuntu-desktop* are just metapackages and can be safely removed. :)

---

### Post by aysiu on 2006-10-26
As I tried to point out in the previous post, it is also opt-in (not opt-out), meaning that you must activate it before it will report anything. It does not report without your knowledge and explicit consent.

---

### Post by FyreBrand on 2006-10-26
> **gruffy-06 said:**
> The "popularity-contest" package is NOT spyware! Even though it may anonymously report to Ubuntu package usage data, NO personal data is ever given away. This data helps the developers decide what to put in main, universe, on the install cd, etc.

I do understand that users who do not want this package installed do not want to help make Ubuntu better for other people. Nevertheless, just remove the *popularity-contest* package. *Ubuntu-base* and *ubuntu-desktop* are just metapackages and can be safely removed. :)One person's definition of spyware isn't the same as another's.  Personally I don't mind letting Linspire know when I activate a new install of NVU or Sun know when I first install Open Office and overall I don't mind letting anyone know when I install their software especially when it's free.

I don't think it's fair or accurate to say that those who don't want enable this utility don't want to help make Ubuntu a better distribution.  I certainly don't think you have any place making that judgment call.  You could definitely say the people who do have it enabled are helpful, but the converse of that statement isn't true (it's also poor logic).

Just to be clear I don't have a problem with supplying this information, but I don't think it's a good idea to be critical of those that are uncomfortable.

---

### Post by iscurrah on 2006-12-31
I was searching for 'popularity contest' for exactly the opposite reason. I like the idea of giving feedback to the Ubuntu developers.

What I'm after though is the results, are these available anywhere? (yes - [http://popcon.ubuntu.com/]("http://popcon.ubuntu.com/"))

btw ... You can turn it on and off via:
System | Administration | Software Sources - a checkbox on the Statistics tab.

---

### Post by ahave2005 on 2007-01-24
Well, I have never heard of it before updating edgy today. There was an update to popularity contest. I searched for it on ubuntuforums and found this thread.

I checked the conf file, and YES I do participate, the problem is....... I've never been asked. I'm actually a bit furious right now. I've not been asked and I've not being told that this package submit information about my system, just check out this statement on popcon.ubuntu.com.

> This package sends the list of packages installed and the access time of relevant files to the server weekly.

If non specified "relevant files" isn't spyware, i don't know. I'm in love with ubuntu, but this is a pretty serious blow for me.

I checked my laptop and a server, they do not participate. Both of them are just upgraded to edgy.

---

