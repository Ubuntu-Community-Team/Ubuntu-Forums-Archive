---
title: "Software Updater"
date: 2014-12-04
forum: Desktop Environments
---

### Post by TWFJR on 2014-12-04
The software updater on Ubuntu 14.10 has frozen up. It shows as green indicating an update but I cannot open by clicking on it. Wondering why this is.

---

### Post by ibjsb4 on 2014-12-04
Sometimes it just gets stuck and
```
sudo apt-get update
```
will get it working again.

If not the case, try opening it in terminal and look for errors.
```
update-manager
```

---

### Post by TWFJR on 2014-12-05
I did **sudo apt-get update** and the Software Updater is still stuck. I also did **update-manager** and this did nothing which tells me something happened but, the Software Updater is still stuck. I will turn off the computer tonight and check tomorrow if it is still stuck.

---

### Post by ibjsb4 on 2014-12-05
You can also try a reinstall.
```
sudo apt-get purge update-manager update-manager-core  && sudo apt-get install update-manager
```

---

### Post by TWFJR on 2014-12-05
Rebooting solve the lock up. Thanks.

---

### Post by mörgæs on 2014-12-05
Good, please mark the thread 'solved'.

---

