---
title: "Compiz fusion extremely laggy after upgrade to 9.04"
date: 2009-05-02
forum: Desktop Environments
---

### Post by Slaskie on 2009-05-02
I upgraded my system from kubuntu 8.10 to 9.04, and after that, everything worked as expected except that compiz fusion is now extremely laggy. My apps are working fine, my dock is smooth, but any compiz-controlled effect (minimizing/maximizing windows, switching workspaces, ring switcher, etc, etc) is extremely choppy (switching workspaces with cube rotate results in my screen freezing for a second then the next virtual desktop appearing). What could have caused the degrade in performance and how can I fix it?

---

### Post by overdrank on 2009-05-02
> **Slaskie said:**
> I upgraded my system from kubuntu 8.10 to 9.04, and after that, everything worked as expected except that compiz fusion is now extremely laggy. My apps are working fine, my dock is smooth, but any compiz-controlled effect (minimizing/maximizing windows, switching workspaces, ring switcher, etc, etc) is extremely choppy (switching workspaces with cube rotate results in my screen freezing for a second then the next virtual desktop appearing). What could have caused the degrade in performance and how can I fix it?

Hi and what is the model of the graphics card?

---

### Post by Slaskie on 2009-05-02
Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by ajgreeny on 2009-05-02
There are major problems with Intel cards and 9.04, I'm afraid.  Some setups seem to manage, but some are completely broken.  Updates may appear soon to fix it but I don't know where you go till then.  If you can get a gui with no compiz, you may need to do that for the time being.

---

### Post by Slaskie on 2009-05-02
Problem solved. I meandered to the Intel Graphics Jaunty link in Overdrank's sig and performed the first two steps: changing my kernel and then updating. I rebooted and compiz was working like magic again. :) Thanks

---

### Post by balloonatic on 2009-05-23
I'm having the same problem. Could you point me in the right direction to the solution you reached?

Thanks.

---

