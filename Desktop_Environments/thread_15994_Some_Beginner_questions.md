---
title: "Some Beginner questions"
date: 2005-02-18
forum: Desktop Environments
---

### Post by charel on 2005-02-18
Hello,
I tried to modify the X-configuration to use all 7 key buttons of the Logitech MX 500 Mouse and something went wrong. 

Now X wont even start; now i just have the text mode after booting.

I did a backup file of the x-config file before doing any changes.

So want I need to do: del the x-config file and rename the backup file.

Can someone please tell me how to do this with the console? (and i use standard installation, so I dont have a root account)

Thank you for any help.

---

### Post by faqpete on 2005-02-18
Hello charel!
try:

sudo cp /etc/X11/XF86Config-4.backup /etc/X11/XF86Config-4

replace "XF86Config-4.backup" with your backupfile without the quotes

faqpete

---

### Post by charel on 2005-02-18
Thank you very much :grin:  Its working again.

---

