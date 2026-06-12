---
title: "Autologin with NO desktop manager"
date: 2007-12-10
forum: Desktop Environments
---

### Post by UmbraMalison on 2007-12-10
Hi all,

I need my ubuntu system to boot without a desktop manager (XDM,GDM,KDM - etc). Autologin as root, start TWM and lauch my application.

i dont want a DM because there is only one user for this system, and OS size is critical.
i do want to login as root, as required by my application. plus my ubuntu is non-persistent to changes (can't be corrupted no matter what the user does) and won't have a network connection. So root login is what i am after. 
TWM is my GUI of choice, due to the size requirements and the user is to only interface with my application and not the GUI.

So at this point, i did the obvious thing. i researched autologin:

[http://ohioloco.ubuntuforums.org/showthread.php?t=303319](http://ohioloco.ubuntuforums.org/showthread.php?t=303319)
[http://ubuntuforums.org/showthread.php?t=634024&highlight=autologin](http://ubuntuforums.org/showthread.php?t=634024&highlight=autologin)
[http://www.shallowsky.com/blog/linux/autologin-upstart.html](http://www.shallowsky.com/blog/linux/autologin-upstart.html)

they all pretty much say the same thing.

create a login script, chmod it for execution, edit tty1 in event.d folder. ive done this about 10 times :confused: an yet i have not had the success others report.

my error is:

init: tty1 main process (3279) terminated with status 1
init: tty1 main process ended, respawning
(both lines repeat x10)
init: tty1 respawning too fast, stopped

of course, returning the tty1 file back to how it started fixes this problem - but obviously i dont have autologin.

i have mentioned this on the other sites, but no response. so i thought a new thread might attract better attention :)

my system is Ubuntu 7.04 (Feisty Fawn).

Thanks for looking,

Andy

---

### Post by UmbraMalison on 2007-12-10
MIGHT have solved it :guitar:

**#note# Feisty ONLY**

i thought, i wonder how the ubuntu live/install disc does it....

edit your tty1 file, found at /etc/event.d/tty1

```
vim /etc/event.d/tty1
```

press insert (on ur keyboard) to change to text mode

scroll down to the bottom file.

replace the exec line for:
```
exec /bin/login -f root </dev/tty1 > /dev/tty1 2>&1
```

i dont know exactly what this line does, i dont know all the parameters. this might not be a good idea???

it works for me.

Enjoy

EDIT#
press esc to return to commands in vim. type ```
:wq
``` to save and exit vim
then REBOOT!

---

### Post by UmbraMalison on 2008-05-09
Also works on 8.04 (Hardy Heron)

Regards,

Andy

---

