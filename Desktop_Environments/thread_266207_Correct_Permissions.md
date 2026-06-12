---
title: "Correct Permissions?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Kurt_Alan on 2006-09-27
**[SIZE="5"][/SIZE]**

I am locked out of my normal session via error message: "$Home/.dmrc file lis being ignored . . . "

What should be my correct permissions for my home directory and for /home/kurt/.dmrc      ??

For my home directory, some are saying 644 and others 755

Thank you!

---

### Post by aysiu on 2006-09-27
I believe .dmrc should be 600

If you have no other valid login, boot into recovery mode and type these commands: ```
sudo chown -R kurt:kurt /home/kurt
sudo chmod 600 /home/kurt/.dmrc
sudo reboot
```

---

### Post by Kurt_Alan on 2006-09-28
****

Changing permissions did enable me for the first time to log into my normal session, however, all text was "garbage," panels were not functioning, etc.  

Now I can no longer log-in, so I'm abandoning trying to solve the problem which I've been working on for about a month.

Is it possible to re-install Ubuntu while leaving all my apps and home directory intact or must I re-format and start over??

Thank you!!

---

### Post by aysiu on 2006-09-28
You can move your /home directory intact if you create a separate /home partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

