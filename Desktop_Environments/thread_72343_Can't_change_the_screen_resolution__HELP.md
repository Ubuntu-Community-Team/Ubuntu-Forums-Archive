---
title: "Can't change the screen resolution  HELP"
date: 2005-10-06
forum: Desktop Environments
---

### Post by zac851 on 2005-10-06
I just got done installing ubuntu 32 bit.   I previously had 64 bit installed but it kept crashing for soeme reason even though I have a 64bit processor.  Anyway my monitor is a 1280x1024 LCD monitor and thats the resolution it ran at when I was running Kubuntu 64 bit.   Now since I've changed to the 32 bit it will only go to 1024x768 and it looks horrible on this monitor because everything is huge.  I edited xorg.conf for the resolution that I wanted but its still not showing when I go to System > preferences >screen resolutions.  What can I do??  THanks

---

### Post by heimo on 2005-10-06
Reconfigure xserver.```

sudo /etc/init.d/gdm stop
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm stop

```

Related instructions:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by zac851 on 2005-10-06
thanks that worked great.  I love this forum

---

