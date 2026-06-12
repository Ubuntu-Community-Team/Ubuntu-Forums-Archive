---
title: "Ubuntu boots, will not load login screen"
date: 2009-02-24
forum: General Help
---

### Post by Zaelyx on 2009-02-24
I have just installed ubuntu 8.10 on my HP Dv4-1225dx Laptop.
It boots fine, loads the boot screen and everything just fine, but then the screen flashes, i see the Ubuntu logo repeated at the top of the screen, hear the noise, but i get no login screen, nothing at all happens after this point. 
It worked fine, after several reboots, not sure what it is now, i rebooted after installing all the updates, and it did not work.

Had to mess around with the alsa-file to make my sound work, got the proprietary driver from ATI for the graphics card.

---

### Post by chmbrs on 2009-02-24
im not sure cause im using mint, but try to boot to recovery mode
and fix x server.

---

### Post by Zaelyx on 2009-02-24
already tried this, now it doesnt play the noise anymore...

---

### Post by chmbrs on 2009-02-24
maybe you can boot in verbose mode.

press "esc" while its booting.

itll display all the messages during boot. you can see what fails to load then search for fix for your problem. i think its something with the display drivers

---

### Post by Zaelyx on 2009-02-25
Tried this, nothing seems to be amiss when booting...everything appears to initialize properly, but the problem still exists

---

### Post by ryofire on 2009-02-25
hmmm check the release notes for the ATI driver you are using If you installed them with the restricted drivers manager they might have an issue with your graphics chipset documented. I've installed 3 different Ubuntu derivatives on my HP DV4-1225DX, and I have not had any problems like that. Not with the latest ATI drivers compiled by a howto or the version installed by the restricted driver manager (which did give me openGL issues though) or even the stock installed drivers. 

Which makes me wonder if you should just download the iso again and burn it on another brand of CD-R :( . Or you could try upgrading from a hardy release. That's essentially what i did.

also check out my thread it may be of limited value for you.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1079111]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1079111")

---

