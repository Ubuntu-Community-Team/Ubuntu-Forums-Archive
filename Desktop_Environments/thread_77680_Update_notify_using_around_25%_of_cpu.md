---
title: "Update notify using around 25% of cpu"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Zotova on 2005-10-17
Anyone got any idea why this my be? It is getting very annoying now and is a problem which didn't exist in Hoary.

Basically as soon as I load up Breezy the fan kicks in, on opening the system monitor you can see that update notifier is taking around 25% of the cpu and the notification are is taking up around 10% of cpu. This makes me wonder if it is a problem with actually displaying the update icon.

[Screenshot Here](http://www.shanghai.me.uk/linux/Screenshot.png)

Help! lol

The only way to cure it is to kill the update process or to uninstall the update manager completly. I have tried doing a complete remove and then reinstalling but the problem still exists. I also do now have any problems installing other software or using apt-get in general.

Thanks.

---

### Post by kaput on 2005-10-17
Have you searched Bugzilla? If you didn't find your particular issue, have you filed a bug so that the developers can fix your problem? They like to do that kind of stuff, you know. :)

[http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/)

---

### Post by Zotova on 2005-10-17
Well considering no one else has reported the problem it would seem a problem related just to my installation and not a bug.

Does have anyone else have any ideas what might be the problem?

---

### Post by nagilum on 2005-10-31
[QUOTE=Zotova]Well considering no one else has reported the problem it would seem a problem related just to my installation and not a bug.

Does have anyone else have any ideas what might be the problem?[/QUOTE]
I experience the same problem from time to time. It happens only rarely and unpredictably and killing and restarting the processes so far always worked. CPU usage goes back to normal after a kill/restart. Guess it's not your installation but actually a bug.

---

### Post by Revert on 2005-11-05
Mine was just doing the same thing, except it was 27-40% range.

---

### Post by djSeverin on 2005-12-07
I've been getting this too. Chews up around 35% of processor and keeps X chewing around the same. Once I kill the process, X drops back to around 4% average and my system returns to normal.

---

### Post by antenagora on 2005-12-08
It happens to me too, but more frequently before breezy was released as stable. Doing an apt-get update && apt-get dist-upgrade -f also fix the problem. It is annoying because it's random.

---

