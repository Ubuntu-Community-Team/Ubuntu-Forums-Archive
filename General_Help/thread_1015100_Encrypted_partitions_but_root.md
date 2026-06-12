---
title: "Encrypted partitions but root"
date: 2008-12-18
forum: General Help
---

### Post by cd-r80 on 2008-12-18
Is it very unsafe use encrypted partitions only for /home & /var & swap & leave root normal so I can easier remote login & switch to other user? (passphrase problem).

---

### Post by jerome1232 on 2008-12-18
Having an encrypted root partition should have no bearing on logging in remotely as it's all unlocked at boot time, the system is for all intents and purposes no diffrent than an unencrypted one after the drives are unlocked during the boot process.

---

### Post by markharding557 on 2008-12-18
I would say it is less secure to have / unencrypted

---

### Post by cd-r80 on 2008-12-19
I mean if I log in as root & then unlock & switch user.

---

### Post by hyper_ch on 2008-12-19
what exactely do you try to achieve?

---

### Post by cd-r80 on 2008-12-19
encrypted /home /var & swap & use ssh to login. without entering passpharase near the PC .

---

### Post by hyper_ch on 2008-12-19
how about: [http://ubuntuforums.org/showthread.php?t=829768](http://ubuntuforums.org/showthread.php?t=829768)

---

### Post by cd-r80 on 2008-12-20
Ok. Just found that encrypted disk on older machine is very slow. Perhaps only /home encrypted for a fileserver.

---

### Post by hyper_ch on 2008-12-20
large read/writing options are slow on any encrypted machines. Altering it just to /home won't change much if the files of the fileserver are in /home.

---

### Post by cd-r80 on 2008-12-20
I just felt that using only Encfs folder was much faster.

---

