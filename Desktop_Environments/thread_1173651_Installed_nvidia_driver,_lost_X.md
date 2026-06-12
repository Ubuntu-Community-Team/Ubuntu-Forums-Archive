---
title: "Installed nvidia driver, lost X"
date: 2009-05-30
forum: Desktop Environments
---

### Post by madchaz on 2009-05-30
Hello all. Having a bit of an issue with the nvidia drivers not working at all. 

Basically, once I have enabled any of the 2 nvidia driver available (173 or 180), next reboot will get me to a console login and kdm trying in an infinite loop to restart X. 

Anyone as an idea?

---

### Post by madverb on 2009-05-30
tail /var/log/Xorg.0.log

Paste the output here.

---

### Post by madchaz on 2009-05-31
Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

