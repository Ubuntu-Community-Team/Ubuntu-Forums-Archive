---
title: "Need help trying to uninstall Macbuntu"
date: 2010-11-17
forum: Desktop Environments
---

### Post by amandaisfun on 2010-11-17
Last week I upgraded from 10.04 to 10.10, and after I did that (went well, no problems) I decided to tweak my display and install macbuntu. Well, I've decided that I don't want it anymore, but when I try to uninstall it, I get stumped.

This is what I got at the command line when I tried to uninstall:

```
amanda@amanda-laptop:~/.macbuntu/10.10-2.3$ ./uninstall.sh

Macbuntu - Mac OS X Transformation Pack

Deinstallation script

Attention!
This script will slide back to default Ubuntu desktop
all Macbuntu-10.10 components will be removed permanently

Checking Ubuntu version...
Passed

Checking currently installed version of Macbuntu-10.10...
Failed. The script is not able to determine what version is currently installed
Exiting...
amanda@amanda-laptop:~/.macbuntu/10.10-2.3$ 

```

This is leaving me totally stumped, and I'd rather not do a fresh install of 10.10 to fix it.

Thanks, also since this is my first post ever, feel free to tell me if I'm doing something wrong...

---

### Post by nick_goodfate on 2010-11-17
You may take an answer by one of the devs . [http://kyleabaker.com/about/](http://kyleabaker.com/about/)

---

### Post by shaunrozario on 2011-04-29
Hi,

If you encounter this problem, open up the uninstall.sh file with a text editor and delete the checkversion() method completely from the start of the brackets to the end of the brackets adn then click on save..This will stop checking the version number and the unistallation process will continue. I Had did an uninstall myself and I was able to do it successfully.. :D

Cheers,

Manchester Utd Rocks!!

---

### Post by FloiT on 2011-04-30
Thanks, **shaunrozario**, but there's an even easiest way to do it: ```
./uninstall.sh force
```
and it'll just ignore the checkversion step.

I have tried and it worked fine (well, the process froze at the end, but everything seems to be all right after a rebooting). I suppose it's better to uninstall macbuntu **before** upgrading Ubuntu :biggrin:

By the way... Man UTd rocks, but Barça rocks more! Visca el Barça i Visca Catalunya! :-D

---

### Post by Scheep on 2011-05-02
**Problems Macbuntu after upgrading to Ubuntu 11.04**

hi all,
After upgrading ubuntu isn´t working like it should anymore. Windows have no borders or buttons and i can´t drag them and the basic ubuntu icons (top of screen) are missing.

So now i¨m trying to **uninstall macbuntu theme** but can find a uninstall file. Tried this way : [http://sourceforge.net/projects/macbuntu/forums/forum/1205032/topic/3819181](http://sourceforge.net/projects/macbuntu/forums/forum/1205032/topic/3819181)
Not working because terminal says i´ve no permission to open file.

any suggestions?
thnx a lot
Erwin

---

### Post by khushy on 2011-05-05
Go to home folder, ctrl  + h , open macbuntu folder, there is a folder 10.10-2.3, right click on it, properties, then in the window copy its address, open terminal, paste this add ( to go to the dir) type: ./uninstall.sh and enter. (if needed add force end of this command)

take care-khushy

---

### Post by khushy on 2011-05-05
i meant add "force at the end

---

### Post by khushy on 2011-05-05
i meant add "force at the end of uninstall command

---

