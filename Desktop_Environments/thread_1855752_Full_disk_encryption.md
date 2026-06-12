---
title: "Full disk encryption"
date: 2011-10-06
forum: Desktop Environments
---

### Post by cavedog on 2011-10-06
I have a ASUS netbook with Lubuntu 11.04 that I use during my lunch break downtown. I really like how snappy it is as compared to Win7 that came with it.  
Here's the thing.  I want to fully encrypt the disk (using alt install) because I'm a paranoid old fool.  Only there isn't an official Lubuntu 11.04 alt install.  I understand there might be an issue with Unity if I used the alt install with that, so I'm wondering if I used the alt-install from Xubuntu, and THEN did the desktop install of Lubuntu and then removed Xubuntu, there shouldn't be any massive drama.

---

### Post by Nostalos on 2011-10-06
Other than if you have an excessively tiny disk it might be difficult.  I've done this a few times myself.  Only issue is if you are extremely determined to remove every possible package installed by xubuntu-desktop package.   Its just a virtual package, so removing it doesnt actually remove anything.  

once installed you should just "apt-get install lubunut-desktop" and be good to go.   If you have the disk space you can even leave them installed side by side and select one or the other from gdm or lightdm (depending on which version you install)

here is some info on removing xfce once lubuntu-desktop is installed.  [http://ubuntuforums.org/showthread.php?t=129517](http://ubuntuforums.org/showthread.php?t=129517)

Also just noticed 11.10 is going to have lubuntu alternate isntaller so might want to wait for release or try the latest ISO if you cant wait
[http://ubuntuforums.org/showthread.php?t=1855749](http://ubuntuforums.org/showthread.php?t=1855749)

---

