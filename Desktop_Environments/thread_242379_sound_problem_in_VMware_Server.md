---
title: "sound problem in VMware Server"
date: 2006-08-23
forum: Desktop Environments
---

### Post by fakie_flip on 2006-08-23
I am having a sound problem in VMware Server. Has anyone had this 
problem? I get the message "Failed to open sound device /dev/dsp: Device or 
resource busy Failed to connect virtual device sound." That happens 
whenever I power on a virtual machine and also when I try to enable sound 
from VMware tools in the XP virtual machine. The only work around for 
this problem I have found was to do `killall esd` before powering on the 
virtual machine. That worked yesterday. Of course I lost all sound in 
Linux untill I rebooted. Today, that is not working when I tried it 
again. I am using Ubuntu 6.06. What is the solution?

---

