---
title: "Using Backed Up Data"
date: 2009-01-07
forum: General Help
---

### Post by BenFischer on 2009-01-07
I have two questions. I little while ago my grahpical display manager broke/got messed up.  And nobody really knew of a way to help me fix it other then reinstall my OS.  If you think this is overkill (like I do), and have an idea [http://ubuntuforums.org/showthread.php?t=1029789](http://ubuntuforums.org/showthread.php?t=1029789) there's the thread.  Anyway if I do have to reinstall I obviously need to back up some data, but I need to avoid backing up the problem and then re-creating it.  My goal is to back up all my application files, and the the driver I had to install for a wireless internet device. My theory is that the only directories I will need are dev, etc, opt, usr, and var.  Would backing up these directories accomplish what I'm trying to do? (I get the feeling that the dev and usr files might contain part of the original problem though?)
My second question is how would I unpack these old directories into my new root directory without massivly messing up my system.  I dont think rm dev, and then cp the old dev in is really a legitimate strategy??  I'll hold out hope though until someone enlightens me.

Thanks,
Ben

---

### Post by cariboo on 2009-01-07
You may be missing a file or two have you tried the reinstall option:

```
sudo apt-get reinstall xserver-xorg
```

this may save you from having to reinstall your distribution.

Jim

---

### Post by BenFischer on 2009-01-08
Thanks for the suggestion but

user@computername:~$ sudo apt-get reinstall xserver-xorg
[sudo] password for user:
E: Invalid operation reinstall

Thats basicly how the output looked from that command.  using --reinstall it was the same.  Does anybody have an answer to my earlier quesiton though?

Thanks,
Ben

---

