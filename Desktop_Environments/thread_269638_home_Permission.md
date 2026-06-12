---
title: "/home/ Permission?"
date: 2006-10-02
forum: Desktop Environments
---

### Post by Flashstar on 2006-10-02
I just changed the permissions of my /home/ directory to get SAMBA to work and now I cannot log back in. How can I change it to let me login again?

---

### Post by jazzgossen on 2006-10-02
Try booting in failsafe mode, which should give you a root prompt. Than you can change the permissions of /home back from there.

---

### Post by PriceChild on 2006-10-02
Once logged into the failsafe:

```
sudo chown <<username>>:<<username>> -R /home/<<username>>
```

---

