---
title: "Dapper/Firefox cannot access Google Docs"
date: 2009-05-31
forum: General Help
---

### Post by dvokt on 2009-05-31
It has been a while but I am sure I was able to access Google Docs from Dapper/Firefox.

This no longer seems to be the case.  I get the following message:

   Sorry, but this browser does not support web word-processing.

Anyone know what is going on here?

BTW, system is up to date.

Thanks,

-Dan

---

### Post by Tibuda on 2009-05-31
What Firefox version? I guess Google Docs implemented some features that won't work in the Dapper Firefox.

Is Dapper still supported?

---

### Post by dvokt on 2009-05-31
Well, I just checked the release date of 6.06LTS Dapper Drake - June 1, 2006.  And though Dapper was the first LTS (Long Term Support) system, 3 years desktop, 5 years server.  I guess it is time for a major upgrade.

The Firefox browser is very old 1.5....

I wish I had figured this out at the beginning of the weekend.  I would have had time to upgrade.

BTW, any suggestions for how to upgrade?  This will be the first time for me.  Should I start from scratch or is there a reliable way to get to the next LTS version (8.10 Intrepid Ibex, I think)?

Thanks for your reply...

-Dan

---

### Post by bjk03 on 2009-05-31
Here is a guide you can follow to upgrade from 6.06 LTS to 8.04 LTS.

[https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS](https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS)

---

### Post by dvokt on 2009-05-31
Thanks bjk03, I juat finished the upgrade and so far so good.

One problem.  I had an fstab entry for a windows share and it seems to be broken:

//192.168.1.101/n$ /media/ts cifs auto,iocharset=utf8,uid=danv,gid=users,credentials=/root/.cifscredentials,file_mode=0777,dir_mode=0777 0 0

Normally this would allow me to access the share using:

file:///media/ts

But there is nothing in that path...

Any ideas?  Probably should start a new thread on this.

Thanks

-Dan

---

### Post by slick_nick on 2009-06-27
2nded. Fully updated Jaunty on an AMD 64bit box. Haven't used google docs for a bit, since the latest distro update, and now I get the "Sorry, but this browser does not support web word-processing. "

---

### Post by Soul-Sing on 2009-06-27
> **danielrmt said:**
> What Firefox version? I guess Google Docs implemented some features that won't work in the Dapper Firefox.

Is Dapper still supported?

I don't think so....
(The servers should not longer be available)

---

### Post by DeMus on 2009-06-27
> **slick_nick said:**
> 2nded. Fully updated Jaunty on an AMD 64bit box. Haven't used google docs for a bit, since the latest distro update, and now I get the "Sorry, but this browser does not support web word-processing. "

Just started Google docs with Jaunty and FF 3.0.11 and it works fine.

---

