---
title: "HDTV Troubles"
date: 2007-12-08
forum: Desktop Environments
---

### Post by felnar on 2007-12-08
Hi all

Having some troubles with my HDTV. I can boot into recovery mode and do sudo /etc/init.d/kdm start...giving me the logon screen, but when i do a normal boot the screen goes blank and the pc becomes unresponsive. I then have to physically reboot the pc. 

I can plug my Generic LCD Monitor in and that works a treat... but i would like to try to resolve the HDTV problem!

I have only been using the OS for about 3days, so i will be grateful for any help recieved


One last thing, which may be of use
I am running dual 8800GTX's with the lastest drivers installed

---

### Post by lsutiger on 2007-12-09
It coulc be the resolution of the HDTV.
Try editing your /etc/usplash.conf file and changing the resolution to the res of the TV.
```
sudo gedit /etc/usplash.conf
```

Worth a shot!

---

