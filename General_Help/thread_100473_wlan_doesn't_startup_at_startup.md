---
title: "wlan doesn't startup at startup"
date: 2005-12-07
forum: General Help
---

### Post by emerick7 on 2005-12-07
I've had some problems with my wireless USB adapter since I installed linux, and every time I boot I have to modprobe ndiswrapper and then go to Admin > Networking to activite the wireless connection.

I've tried ndiswrapper -m as well as putting ndiswrapper in /etc/modules, but nothing seems to work.  It's been getting aggrevating to set it up every time.  Any ideas on how I can get it working?  I'd greatly appreciate that... thanks!!

---

### Post by emerick7 on 2005-12-07
need help please!!! anybody know anything I can try??

---

### Post by teaker1s on 2005-12-07
you coul create a script in init.d and use update rc.d to run it everytime you boot  that's how my extra keyboard keys are mapped

---

### Post by emerick7 on 2005-12-07
teaker1s - would you be able to tell me how to that?? sorry, but since I'm new to linux that went over my head, but I'd like to learn... thanks!

---

