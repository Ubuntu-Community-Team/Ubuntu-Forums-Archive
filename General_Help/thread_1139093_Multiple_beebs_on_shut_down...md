---
title: "Multiple beebs on shut down.."
date: 2009-04-26
forum: General Help
---

### Post by kibster on 2009-04-26
I get multiple beebs on shut down   they so fast sounding that I can hardly count them , but it sounds like 4 quick beebs. 
Theres nothing that I have found in archives .  If I'm missing something someplace let me know to get me on the right track. 
POST beebs are fine. Just when shutting down that I get the beebs.

Your help would be greatly appreciated. 


Russ

---

### Post by cwbar_1 on 2009-04-26
Edit the /etc/modprobe.d/blacklist.conf file.  (sudo gedit /etc/modprobe.d/blacklist.conf) Add the line (without quotes) "blacklist pcspkr"  Reboot and next shutdown will be quiet.  I don't remember where on this forum I found the fix, but Kudos to the originator.

---

