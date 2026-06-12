---
title: "upgrading from 11.04 to 11.10 froze, safe to restart"
date: 2011-11-02
forum: Desktop Environments
---

### Post by Foeburner on 2011-11-02
I was upgrading from 11.04 to 11.10 and when it got to the Install the Upgrades section and said about 5 minutes remaining, the process asked me if I want to keep or replace PPTPD.conf. 

Well i tried clicking on Keep but it wouldnt do anything. I am stuck on this screen and cant do anything to the computer. 

Should I restart it? I dont want to damage any of my conf files. Is there anything I can do?

Currently, there are others pending on this machine as i have shared files available for them so wiping is not an option. 

All feedback is appreciated!

---

### Post by Foeburner on 2011-11-04
For those with this same issue, I had to force restart and came up as 11.10 but i had issues with many things, noticibly my ftp and vpn servers. 

When i tried to reinstall them it gave me an error but told me to run 

```
sudo dpkg --configure -a
```

That did the trick.

Hope this helps someone.

---

