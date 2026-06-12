---
title: "New User Cannot Login with GDM"
date: 2005-11-13
forum: Desktop Environments
---

### Post by MiddleBrooker on 2005-11-13
Hi,
I'm trying to set up a new Standard User like the normal one that the Ubuntu Breezy Installation set up.
I've added it via System --> Administration --> User and Groups but when I logout and try to login with the new one I'll get some error messages:

1) the .dmrc file has incorrect permission and will be ignored
2) GDM was unable to write into my authorization file due permission problems or low disk space

What can I do?
I don't understand the problem, because I've already tried to change permission in the /home/NEW_USER_FOLDER  also I would like to copy all the root profile that I've used now for setup the fresh installation [Background - mail - programs settings - etc.... all the configuration files that I've actually into my root folder].

Thanks for any suggestion.

---

### Post by aysiu on 2005-11-13
Does this help?
[http://www.ubuntuforums.org/showthread.php?t=77627](http://www.ubuntuforums.org/showthread.php?t=77627)

---

### Post by teaker1s on 2005-11-13
while it may not be the solution I corrupted a user account and when I created a new one it went balistic the solution I found was to reinstall 'adduser' and restored account creation settings

---

