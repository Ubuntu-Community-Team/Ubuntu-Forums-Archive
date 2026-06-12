---
title: "Lightweight virtualization for &quot;desktop security&quot;"
date: 2010-09-02
forum: Desktop Environments
---

### Post by Leeteq on 2010-09-02
Hi all, I wonder which linux distros that can best fit for the following scenario using VirtualBox OpenSource Edition (OSE) on Ubuntu 10.04 LTS:

I want to run applications that need web access separately, not giving them access to the main document archive, etc., so I want to run Firefox in one virtualized instance, and Pidgin in another, so that in case of security issues, nothing that can sneak in through one can affect or destroy things in the other, and not on the main "host" (Ubuntu).

Virtualbox instance examples:
- Browsing (Firefox and Opera browsers with multimedia tools/features and web access)
- Email: Thunderbird in its own instance with web access.
- Instant Messaging: Pidgin and Skype. (just that, in a separate instance...)
- Web development: LAMPP, in an instance without network/web access.

Main purpose is to spread security risks into separate contained environments, and also have them launch as fast as possible, without more drivers or the like loaded than strictly necessary for that instance's particular focus. 

For this **I look for something _really_ lightweight**. 

**I have done some googling, and have found the following:**
(before I start testing, I would like to hear if some of you have some comments and suggestions that may save me some time)

[http://en.wikipedia.org/wiki/Ubuntu_Minimal_Desktop](http://en.wikipedia.org/wiki/Ubuntu_Minimal_Desktop)
[http://en.wikipedia.org/wiki/Tiny_Core_Linux](http://en.wikipedia.org/wiki/Tiny_Core_Linux)
[http://bengross.com/smallunix](http://bengross.com/smallunix)
[http://www.linuxfromscratch.org](http://www.linuxfromscratch.org)
[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)

By the way; wouldn't it be practical with a separate forum for virtualization here?

---

### Post by LowSky on 2010-09-02
use Puppy or DSL

---

### Post by CPL2010 on 2010-09-02
I prefer Puppy as it's prettier, DSL is just as functional though.  For the security side though, you want to have two seperate environments to accomplish different goals.  You will have to start to think about segmenting your "network" on your desktop by forcing routes and rules on the firewall.

I don't know what your setup is, but the easiest is to create a DMZ on your physical router.  It's usually a check box and then you assign an external IP address to it.  That way it's sitting "outside" the firewall.  You give the VM the IP address it needs to live outside the firewall, after you configure that you can do other neat things like bind a mac address and use DynaDNS.

For myself I have the Wireless router in my house (POS 30 buck Linksys) enable the DMZ in the configuration and allow DHCP on the VM host to grab the IP address from the ISP.  From this point I assign my dyna DNS account info and I now have a website outside my internal network.

I would post it, but it's a circumventor portal.  And I'm hesitant to offer up my home proxy setup to the world by pointing it out.  however the same setup allow me to have an "airgap" back into my home environment so I can grab stuff from my LAN while on the road.

---

### Post by benerivo on 2010-09-02
> **Leeteq said:**
> By the way; wouldn't it be practical with a separate forum for virtualization here?

There is a separate forum for virtualization...
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

