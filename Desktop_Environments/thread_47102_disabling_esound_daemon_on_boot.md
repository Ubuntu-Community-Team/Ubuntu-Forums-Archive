---
title: "disabling esound daemon on boot"
date: 2005-07-07
forum: Desktop Environments
---

### Post by mattb_ on 2005-07-07
I have been having only trouble with esound and have been killing the process manually to get sound working with ccertain applications including the flash-plugin. Basically nothing works when it is running apart from rythm box.
Can anyone tell me how to disable it?
Thanks.

---

### Post by varunus on 2005-07-07
Killing esound is not the correct solution to this.  Instead, you should follow this howto:

[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)

Step one of that howto shuts off ESD, if you want to know how, but it is not required.  (I wrote the original howto that one is based off of.)  Instead, just follow the rest of the steps in the howto, and all of your sound should work.

Flash itself has a bug in it that stops sound from playing, to fix it, type the following at the console:
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

Enjoy.

---

