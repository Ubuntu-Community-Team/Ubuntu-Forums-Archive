---
title: "KDE Control Centre &quot;Admin Mode&quot; Problem"
date: 2005-04-18
forum: Desktop Environments
---

### Post by finster on 2005-04-18
Hi all,

I am having a problem getting into any of the "Administrator Modes" in KDE Control Centre (ie Samba, Login Manager etc.) After I have clicked the button, I just stuck on a screen with a red border and "Loading..." in it.

I have had a look in /var/log/messages and this is what appears: -

Apr 18 21:55:19 localhost sudo: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=pts/5 ruser= rhost=  user=andy
Apr 18 21:55:56 localhost sudo:     andy : TTY=pts/4 ; PWD=/home/andy ; USER=root ; COMMAND=/usr/bin/kdesu_stub -

Anybody got any ideas?

Thanks.

---

### Post by NTolerance on 2005-04-18
[http://ubuntuforums.org/showthread.php?t=26444](http://ubuntuforums.org/showthread.php?t=26444)

---

### Post by finster on 2005-04-18
[QUOTE=NTolerance][http://ubuntuforums.org/showthread.php?t=26444](http://ubuntuforums.org/showthread.php?t=26444)[/QUOTE]

Thanks. I did do a search, but couldn't find anything similar.

Deleting the folder as mentioned in the other thread fixed it.

( rm -rf /var/tmp/kdecache-username )

---

### Post by NTolerance on 2005-04-18
[QUOTE=finster]Thanks. I did do a search, but couldn't find anything similar.

Deleting the folder as mentioned in the other thread fixed it.

( rm -rf /var/tmp/kdecache-username )[/QUOTE]

I've had to delete the file repeatedly.   :-|

---

