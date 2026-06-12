---
title: "ServAuthDir problem"
date: 2007-11-12
forum: Desktop Environments
---

### Post by stjoenewt on 2007-11-12
All,

I was recently messing around with /var permissions and in the process hosed things up.   :(   When I boot now, I get the following message;

"Server Authorization Directory (daemon/ServAuthDir) is set to /var/lib/gdm but this does not exist.  Please correct GDM configuration and restart GDM."

I have gone into a terminal session and see the directories called out in the message.  An "ls -l" command displays the information below;

drwxrw-rw- 16 root  root  4096  2007-04-15  08:11  var
drwxr-xr-x  45 root  root  4096  2007-10-28  07:45   lib
drwxr-x---   3   root  root  4096  2007-11-11  17:32  gdm

The GDM directory contains two hidden files and no visible files.

I have tried removing and re-installing GDM (sudo apt-get remove gdm & sudo apt-get install gdm) and reconfiguring GDM (sudo dpkg-reconfigure gdm) with no success.

I suspect the problem is not that the directory isn't there, but just not visible to GDM.   

Thanks in advance for any assistance.

---

### Post by morgan_greywolf on 2007-11-12
Try this. In a terminal:

```
chgrp gdm /var/lib/gdm
chmod 770 /var/lib/gdm
chmod o+t /var/lib/gdm

```

That directory must be owned by group gdm, and have group write permissions so that the gdm user can write to it.  The sticky bit should be on too.  The above will take care of this for you.

---

### Post by stjoenewt on 2007-11-12
morgan_greywolf, et. al.,

Thanks for the quick response.

I did the chgrp and chmod commands you sent.  However I still get the same error on booting.  The directories named have the characteristics noted below;

drwxrw-rw-  16  root  root  4096  2007-04-15  08:01  var
drwxr-xr-x   45  root  root  4096  2007-10-28  07:45  lib
drwxrwx--T   3  root  gdm   4096  2007-11-11  17:32  gdm

I then looked at the hidden files in GDM, their settings are as follow;

drwxr-x---     3   gdm   gdm  4096  2007-11-11  17:32  .
drwxr-xr-x  45  root  root  4096  2007-10-28  07:45  ..
-rw-------       1   gdm   gdm   33  2007-11-08  18:20  .cookie
drwxr-xr-x    2   gdm   gdm  4096  2007-08-28  22:20   .fontconfig

Do I need other files in the GDM directory?  I had seen another post that referred to ":0.Xauth" and ":0.Xservers", however I don't know if those are relevant to my install.

Thanks in advance for any suggestions.

---

### Post by stjoenewt on 2007-11-12
When I installed, I setup several partitions, and mapped specific directories to them.  I have a separate partition for /home, /var, /usr etc.   I suspect that the /var partiiton is not mounting properly and as a result being mounted readonly.

Is there a way to prove or disprove this?

Thanks for any advise.

---

### Post by stjoenewt on 2007-11-13
I found out how to see the characteristics of the mounted partitions, and my /var partition is indeed mounted RW.   So much for that theory.  I have noticed however, if I change the GDM configuration to use a directory I created on another partition, it does start.  It's appearance if different, it displays a different log on screen, a blue one with a yellow flower, but it does start successfully.   

This leads me to suspect that somehow GDM is remembering old directory settings, like the group name and/or access permissions.   Does anyone know of a cache, or temporary settings somewhere that I must clear?   It obvious survives across a shutdown, so it can't be RAM or other memory buffers.

Thanks for any assistance anyone can provide.

---

