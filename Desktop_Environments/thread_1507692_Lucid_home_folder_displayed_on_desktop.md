---
title: "Lucid: home folder displayed on desktop"
date: 2010-06-11
forum: Desktop Environments
---

### Post by frpweiss on 2010-06-11
Help! Using Ubuntu Lucid 10.04
System froze, and after reboot, my homefolder is displayed on my desktop.
Need help to show clean desktop once again.
I'm a complete novice at ubuntu.
Thanks

---

### Post by gingivere0 on 2010-06-11
Try this out:

```
sudo add-apt-repository ppa:tualatrix/ubuntu-tweak
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

Then go to Applications>System Tools>Ubuntu Tweak.  Look on the left side under **Desktop** and Desktop Icons.  There, you can customize your Desktop Icons.  Good Luck! :)

---

### Post by frpweiss on 2010-06-14
thanks gingivere0
tried ubuntu tweak, but no change . . 
works when I log in as a different user, but not when logged in as primary user
also tried gconf-editor - changing desktop_is_home_dir, but with no effect

---

### Post by frpweiss on 2010-06-14
Problem solved
Used ubuntu tweak to reset default folder location, then under desktop icon setting unclicked 'show contents of homefolder on desktop', and miraculously, on logging out, system restored.
Thanks for help.

---

