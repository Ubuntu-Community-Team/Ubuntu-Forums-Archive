---
title: "Flash and MPG files"
date: 2006-07-10
forum: Desktop Environments
---

### Post by user50310 on 2006-07-10
Hello everyone. I'm curently using Ubuntu 6.06 and Windows XP Pro (dual boot). When it comes to Linux I'm a complete newbie and that's sad because I have tried many times before to switch completely to Linux but obviously I failed.

I installed Kubuntu 6.06 yesterday but it seems to me that Ubuntu is more popular and has better support community (judging by the number of HOW TOs available at least). That's why I installed Ubuntu.

I can't get flash to work with Firefox 1.5.0.4 and I don't know how to enable playback of 'restricted formats' (mpeg, avi, qt etc).

Other than that Ubuntu has recognized all of the hardware including my printer too. 

I tried running the flash installer and it installs successfully but Firefox thinks it's not there.

I would really appreciate your help.

Thanks.

---

### Post by sgbeamer on 2006-07-10
This will take care of all your problems

[http://www.ubuntuforums.org/showthread.php?t=190025&highlight=turn+ipv6](http://www.ubuntuforums.org/showthread.php?t=190025&highlight=turn+ipv6)

---

### Post by user50310 on 2006-07-15
Sorry about the late reply. I get the following error when trying to install it



user@computer:~$ sudo apt-get install automatix
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by kpkeerthi on 2006-07-15
Do not run more than one package manager at the same time. If you are running apt-get or aptitude, make sure you close synaptic and update manager. Run only one of these at the same time. Also, run command line package managers(dpkg, apt-get, aptitude) as super user.

---

### Post by user50310 on 2006-07-17
AFAIK I'm not running anything else...

---

