---
title: "System Preferences not Restored"
date: 2010-03-15
forum: Desktop Environments
---

### Post by fgrazi on 2010-03-15
My system does not save preferences. This includes, for example, keyboard shortcuts, Power management configuration, Network connections … I can change them (any parameter) but when I reboot my system all changes are lost. 

I am using Gnome 2.28.1 under Ubuntu 9.10

 Note: this can have been caused by a previous mistake. In changing keyboard shortcuts I tried to delete an entry with the Del key. Instead Ubuntu assumed I assigned Del as shortcut. Being unable to reset that fact I created a second user and copied .gconf and .gconfd folders from it.
 
 Anybody has an idea of what can be going on? Any way to fix this problem, or at least a link to some documentation about .gconf and .gconfd content?
 
 Thanks
 
 franco

---

### Post by mcduck on 2010-03-15
How did you copy those directories? Check that they are owned by your own user and have correct permissions...

(If you, for example, copied them as root the copied directories would be owned by root and that would mean that your own user doesn't have permissions to write to them, so it's not able to store any settings)

---

### Post by colleenElizabeth on 2010-03-15
I had the same problem when I first installed Ubuntu.  I did it from a bootable USB and unless I removed that USB my settings were re-set every time.

Also, I deleted all my users and just have one that is always booted on start up and now it saves every time.

---

### Post by fgrazi on 2010-03-15
Thanks mcduck & Elizabeth,

That was exactly the problem, I changed ownership of both folders & their content and problem was solved!

---

