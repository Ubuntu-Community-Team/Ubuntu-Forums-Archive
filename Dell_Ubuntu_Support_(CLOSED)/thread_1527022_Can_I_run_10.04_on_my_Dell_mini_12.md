---
title: "Can I run 10.04 on my Dell mini 12?"
date: 2010-07-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BettyMulc on 2010-07-08
I currently have the dell version of 8.04 and would like to go to Ubuntu 10.04 LTS.  I have experienced and also read that there is no upgrade path but see conflicting but old comments about running std ubuntu distros on the minis - problems with video drivers, etc...
 
Can I wipe the Dell OS and install 10.04 and have eveything work correctly (video, audiom wired and wireless LAN, etc...)?

---

### Post by bhadams1 on 2010-07-08
I have a Mini 9 and have upgraded from 9.xx to 10.04, but I did my upgrade via the Update Manager.  So far the only existing problem I have experienced is that my SD drive just disappeared, and I haven't found a way to make it reappear.  Everything else works just fine.

---

### Post by mikewhatever on 2010-07-09
I wonder if Dell provides an upgrade path. bhadams1, was yours an OEM Ubuntu install? Upgrading Dell's minis should prove rather complicated, since Dell used to preinstall the lpia architecture of 8.04, which had since been abandoned. Further difficulty arises from the mini 10/12's graphics chip, gma500, aka Poulsbo. Intel has been selling it to OEMs since about 2008, but has been refusing to provide adequate driver support for Linux. At the moment, there are two distros that have gma500 support out of the box: Mandriva 2010 and Jolicloud. The following Ubuntu releases can be made work with various success: Jaunty, Karmic, Lucid, but none work out of the box.
To summarize, if Dell provides an upgrade path, go ahead and upgrade. If not, your best shot is to back up the files and reinstall Mandriva or Jolicloud. In case you want Ubuntu, I'd recommend Karmic.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by bhadams1 on 2010-07-10
Hello mikewhatever,

Yes my ubuntu was OEM installed--I specifically purchased my Mini 9 with Ubuntu back in March 2009.  The Update Manager is set to view updates, and when the new OS comes out, it gives me an option to update.

The only problem I have not is my built in SD drive is missing and I can't get it back.  But everything is working fine.

---

### Post by mikewhatever on 2010-07-11
Hi bhadams1,
the question is, does Dell provide an upgrade path for its lpia Ubuntu spin, or did you have a regular i386 preinstalled. I'd be much obliged if you could post the output of the following command:
```
uname -m
```
.

---

### Post by bhadams1 on 2010-07-11
i686 is what the code manifested.  Does this help?

---

### Post by mikewhatever on 2010-07-11
Yes thanks. That's the standard 32bit version, not lpia.
Anyway, reinstalling Ubuntu is really not that hard, however, the other problem, gma500, is a vicious beast.

---

### Post by K-Sub on 2010-07-11
FYI, I installed the 10.04 Netbook Remix on my Dell Mini 10v to replace the 8.04 that came on the machine.  10.04 is a much better and refined system.  It works quite well, and everything works (including my SD slot.)  I installed it from a thumb drive and it was pretty quick and easy.

---

### Post by mikewhatever on 2010-07-11
> **K-Sub said:**
> FYI, I installed the 10.04 Netbook Remix on my Dell Mini 10v to replace the 8.04 that came on the machine.  10.04 is a much better and refined system.  It works quite well, and everything works (including my SD slot.)  I installed it from a thumb drive and it was pretty quick and easy.

Glad everything worked for you. Of cause, mini 10 and mini 10v are different models, though they look very similar from outside. The former has Z500 Atom cpu with gma500, while the latter, N270 Atom cpu with gma950. Accidentally, Dell mini 12 is also packed with gma500.

---

### Post by hedgeborn on 2010-07-11
> **BettyMulc said:**
> I currently have the dell version of 8.04 and would like to go to Ubuntu 10.04 LTS.  I have experienced and also read that there is no upgrade path but see conflicting but old comments about running std ubuntu distros on the minis - problems with video drivers, etc...
 
Can I wipe the Dell OS and install 10.04 and have eveything work correctly (video, audiom wired and wireless LAN, etc...)?

I have a Dell Latitude 2100 netbook which is a close cousin to the Dell Mini 9 and 10 and I was able to successfully upgrade from the Dell version of 8.04 to Ubuntu 10.04. The only issue I had was a small problem with the broadcom wireless driver which I was able to resolve in 10 minutes just by searching this forum and updating/downloading a driver through the terminal. I'm an extreme newbie and I was able to pull it off. Everything else worked perfectly without any futzing about. You'll find the flash support (youtube videos etc) much better on 10.04 along with some other nice improvements.

---

### Post by ronewolf on 2011-05-28
> **mikewhatever said:**
> .... At the moment, there are two distros that have gma500 support out of the box: Mandriva 2010 and Jolicloud. The following Ubuntu releases can be made work with various success: Jaunty, Karmic, Lucid, but none work out of the box.
To summarize, if Dell provides an upgrade path, go ahead and upgrade. If not, your best shot is to back up the files and reinstall Mandriva or Jolicloud. In case you want Ubuntu, I'd recommend Karmic.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Of everything that I've read over the past 2+ years on the Mini 12 Ubuntu upgrade issue, this is by far the clearest statement. THX!!

Tho the quote a bit further down in the thread "reinstalling Ubuntu is really not that hard, however, the other problem, gma500, is a vicious beast." is to be admired as well.

A year out, nearly June 2011, has anything changed? Can you recommend a more recent thread on the issue. Or, grimly, not?

---

### Post by Cowchip7 on 2011-05-29
I installed 10.04 LTS on my mini 9. I booted from USB. I installed 2 partitions: one for my home folder and one for the OS. Installation was as simple as pie. You may need to use a wired internet connection to install the wireless driver. [www.ubuntumini.com](www.ubuntumini.com) will walk you through everything.

---

