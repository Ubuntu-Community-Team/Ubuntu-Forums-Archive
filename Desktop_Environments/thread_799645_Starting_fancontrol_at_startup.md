---
title: "Starting fancontrol at startup"
date: 2008-05-19
forum: Desktop Environments
---

### Post by lordfkiller on 2008-05-19
Hi everyone.

I want to start /etc/init.d/fancontrol at startup. (command: sudo /etc/init.d/fancontrol start) But since the service must be started by an administrator(sudo or gksudo), I have to start it manually even if I set it to be run at startup. What should I do?

Any help is kindly appreciated.

---

### Post by MGStreak on 2008-05-27
> **lordfkiller said:**
> Hi everyone.

I want to start /etc/init.d/fancontrol at startup. (command: sudo /etc/init.d/fancontrol start) But since the service must be started by an administrator(sudo or gksudo), I have to start it manually even if I set it to be run at startup. What should I do?

Any help is kindly appreciated.

[http://ubuntuforums.org/showpost.php?p=219205&postcount=1](http://ubuntuforums.org/showpost.php?p=219205&postcount=1)

It's the last 'tip' in this HOWTO.

Also, don't forget the last tip here:
[http://ubuntuforums.org/showpost.php?p=4086622&postcount=59](http://ubuntuforums.org/showpost.php?p=4086622&postcount=59)

Otherwise the script will not be executable!

Hope this is what you were looking for!

---

