---
title: "Help!  I Changed Home Folder Permission Level"
date: 2008-07-09
forum: Desktop Environments
---

### Post by umechanism on 2008-07-09
Let's just say that I altered my permission levels on my home folder and now I can not even login to my desktop after fresh reboot.  It's a long story that I won't go into here.

My question is - what permissions should be set on the home folder and those folders below it?  0777?  0644?

Please help!
(sent from a WinXP machine)

Mike

---

### Post by mikewhatever on 2008-07-09
According to ls -l of my home, the permissions are 755. You can apply that recursively with -R switch. <sudo chmod -R 755 /home/your-user-name>.

---

### Post by umechanism on 2008-07-09
Thank you.  That worked!  I did not use the -R but it worked just fine.  I'm back on the air.

Mike

---

