---
title: "xcompmgr great lagg"
date: 2005-08-31
forum: Desktop Environments
---

### Post by JOKe on 2005-08-31
when i start xcompmgr with -c or -C the lag is GREAAAAAAAAAAAT i know that the lag is big with transperancy so i will not start it but dropshadows ??? :( 
why is this lag ? 
when i install nvidia driver and make Driver "nvidia" from "nv" X dont want to start if extendsion for xcompmgr is enable so ?? whats can i do
;+(

---

### Post by frodon on 2005-08-31
did you add the **Option 		"RenderAccel" 		"true"** option ?, with a nvidia card xcompmgr should work without any lag.
I think xcompmgr use your CPU power instead of use your card acceleration and it's why it lags
Post your xorg.conf file to get more help.

---

