---
title: "How to know the current settings of Monitor?"
date: 2005-04-20
forum: Desktop Environments
---

### Post by globalspace on 2005-04-20
Hi all,
i'm reading a lot of How to and i lovin' it  :smile: 
Well, my question is :
**How to know my current Setup/Settings of My Monitor ?** 
i'm using the fglrx driver (for the 3d acceleration of my ati 9800pro) and i can't change the resolution <on the fly> ... i don't care for this but i only whant to know my current refresh rate ....

Thanks a lot
 O:)

---

### Post by heimo on 2005-04-20
I can't verify this at the moment, but I believe xvidtune shows also the currect refreshrate. Some monitors also show the refreshrate when mode is changed (maybe in some menu too?). xvidtune may require vidtune-extension to be loaded in xorg.conf
 
You probably could also check the xorgs logfile in /var/log/ and see which mode was selected (typically named after resolution and refresh rate).

---

### Post by globalspace on 2005-04-20
[QUOTE=heimo]I can't verify this at the moment, but I believe xvidtune shows also the currect refreshrate. Some monitors also show the refreshrate when mode is changed (maybe in some menu too?). xvidtune may require vidtune-extension to be loaded in xorg.conf
 
You probably could also check the xorgs logfile in /var/log/ and see which mode was selected (typically named after resolution and refresh rate).[/QUOTE]


heimo thanks a lot !!!
in my SyncMaster's Monitor Menu i can see the current setup ...
i'm very stupid  :roll:  :-P 

thanks again !

---

