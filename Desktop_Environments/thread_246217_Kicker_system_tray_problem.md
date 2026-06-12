---
title: "Kicker system tray problem"
date: 2006-08-28
forum: Desktop Environments
---

### Post by mike1821 on 2006-08-28
Hi all, 

I am using kubuntu 6.0.6 with kde 3.5.2. After the system finish booting up and after logging in, I cannot see my system tray icons.

If i do:

sudo pkill -9 kicker

and then,

sudo kicker 

The system tray works ok. However, If I run "kicker" without sudo then the problem remains. Any ideas would be really helpful.

Thanks in advance,
Mike

---

### Post by Ptero-4 on 2006-08-28
Try clearing your ~/.kde folder (you may need to use sudo for that). The permissions in that folder might have gone bad and kde have issues with it's stuff.

---

### Post by mike1821 on 2006-08-29
This worked for me.

Thank you very much Ptero-4

---

