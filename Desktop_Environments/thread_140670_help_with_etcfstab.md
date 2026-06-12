---
title: "help with /etc/fstab"
date: 2006-03-06
forum: Desktop Environments
---

### Post by tophat2445 on 2006-03-06
ok, this might be a little redundent, but how do I get permissions to save the changes that I've mande to my /etc/fstab file....I really need to know this...I have ALOT of data in on of my disks...I've already made the appropriate changes, I just need to save them...but how.

Thanks, 
Kenny

---

### Post by christhemonkey on 2006-03-06
you need to open it with root/sudo
```
sudo gedit /etc/fstab
```

---

### Post by tophat2445 on 2006-03-06
thanks alot...you da man...

---

### Post by issueperson on 2006-03-06
whatever you do, back it up before you change it.

sudo cp /etc/fstab /etc/fstab_backup

if you mess up your fstab and don't have a copy, it can be a big pain to get it working again.

---

