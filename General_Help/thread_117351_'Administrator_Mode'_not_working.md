---
title: "'Administrator Mode' not working"
date: 2006-01-14
forum: General Help
---

### Post by m33p0n3 on 2006-01-14
Alright, so I just installed Breezy from the DVD, which I grabbed last night.  Everything seems to work fine, except I've had to change all of my settings from the command line, because the System Settings won't go into "Administrator Mode" as it calls it.

At first when I clicked it, it would return with "su returned with an error".  Did a quick google, found this forum, and this thread specifically: [http://ubuntuforums.org/showthread.php?t=80921](http://ubuntuforums.org/showthread.php?t=80921)

Changed my hosts file from just "127.0.0.1 localhost" to "127.0.0.1 localhost.localdomain localhost ubuntu".  Went back and tried to use it again, only it came up with "Conversation with su failed".  Another quick search on this forum came up with this thread: [http://ubuntuforums.org/showthread.php?t=116514](http://ubuntuforums.org/showthread.php?t=116514)

Sure enough, I added my user account by adding "brian ALL=(ALL) ALL" to my /etc/hosts file.  Went back and tried to use the administrator mode button, and it now prompts for the password, then after one is put in it sits there for a few seconds then goes back to the screen like nothing had happened.  :confused: 

Perhaps there is something wrong with the sudo package? I'm not too sure where to go with this.  I appreciate any help I can get.

---

### Post by vanhonk on 2006-01-14
I'm having the exact same problem.
 
Update: I just did all my adept updates and it seems to have fixed it. Adept gave me a few errors, but I continued and it updated.

---

### Post by bored2k on 2006-01-14
The default KDE has this major bug. To fix this, you need to upgrade Kubuntu to the latest 3.5 version. [http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

---

### Post by m33p0n3 on 2006-01-14
[QUOTE=bored2k]The default KDE has this major bug. To fix this, you need to upgrade Kubuntu to the latest 3.5 version. [http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)[/QUOTE]

Oh, alright.  Thanks for the quick response.

---

### Post by sharke on 2006-01-14
You can use the default system settings for kde by typing kdesu kcontrol in terminal.
Regards
Sharke

---

