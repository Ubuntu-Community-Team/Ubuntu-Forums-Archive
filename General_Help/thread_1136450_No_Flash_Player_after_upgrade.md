---
title: "No Flash Player after upgrade"
date: 2009-04-25
forum: General Help
---

### Post by paydaydaddy on 2009-04-25
Upgraded to 9.04 and have spent hours trying to get flashplayer to work(youtube). Have searched the forums and tried numerous recommended fixes to no avail. I am open to suggestions. Got any?

---

### Post by conscious on 2009-04-25
Assuming you have Adobe's player, have you tried
```
sudo dpkg-reconfigure flashplugin-installer
```
?

---

### Post by paydaydaddy on 2009-04-25
Thanks conscious, that did the trick. I ran the command and then tried a youtube video. It would not play. I re-started X and then it worked.

---

