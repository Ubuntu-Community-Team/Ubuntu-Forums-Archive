---
title: "No network after updates"
date: 2005-12-07
forum: General Help
---

### Post by HeavyAl on 2005-12-07
I ran the package updater from the little icon that says there are updates and it did its thing and seemed to be ok when it finished (no errors in the log yada yada).

One of the updates was for the kernel so I rebooted the machine and when I came back up my connection no longer worked.

The network connection is through a dlink card in the machine that hooks to a switch and then that switch (another crappy but function dlink) hooks to my router (crappy but functional linksys wired/wireless). Everything works fine with the other machines hooked to the router and through the switch so I doubt its a hardware issue (not to mention the connection worked fine before the reboot).

So now I cant ping the router, even though network settings/connections shows eth0 as being active. The system also fails to retreive the time on boot. Network gets initialized but I just cant seem to get out of the box.

Anyone had a similar issue or some tips on what else I might check?

---

### Post by HeavyAl on 2005-12-09
Forget it. 

Guess it turned out to be a hardware problem after all. It just happened to coincide with my updates. 

The router took a dump. After resetting it everything works fine again.

/me slaps self on back of head

Bottom line: Ubuntu still rocks.

---

