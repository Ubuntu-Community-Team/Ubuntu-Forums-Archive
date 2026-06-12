---
title: "Mount without password (NTFS partition)"
date: 2010-07-02
forum: Desktop Environments
---

### Post by efAston on 2010-07-02
Hi all,

I have my NTFS partition set to automatically mount in my Kubuntu Lucid installation, but it always prompts me for a ksudo password when I boot before it mounts. Is there any way of getting it to mount without a password? As it is, I need to copy desktop wallpaper images and save torrents to my ext4 or the password prompt makes a mess of everything when I boot up.

Cheers,
Aston

---

### Post by Greggi on 2010-07-02
You can also remove the password of the user account, or?

---

### Post by Morbius1 on 2010-07-02
You might want to post the output of the following commands so everyone can see how things are configured:

```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```If you used some GUI app to automount like mountmanager, Pysdm, or others it's likely that it discombobulated things.

---

### Post by efAston on 2010-07-02
I tried entering a NULL password for my login to see if that would help, but it only works with KWallet, Kubuntu doesn't allow you to have a NULL login password. Anyway adding it to fstab worked, if only the KDE device manager worked as well!

---

### Post by efAston on 2010-07-02
Thank you!

---

