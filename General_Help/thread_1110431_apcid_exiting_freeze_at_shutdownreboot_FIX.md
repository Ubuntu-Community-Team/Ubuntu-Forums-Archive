---
title: "apcid: exiting freeze at shutdown/reboot FIX"
date: 2009-03-29
forum: General Help
---

### Post by MajorTom00 on 2009-03-29
Well, this is hardly a fix. This considers users of Ubuntu 8.10. I had just done the upgrade the other day. I'm running a server (using desktop edition, I'm still quite new to linux), so after installing and configuring several packages via ssh, I called a reboot of the system using:

 ```
reboot
```

However, after ten minutes of being unable to log in, I went down to the bowels of my cellar to where the server resides, turned on its monitor to see "apcid: exiting" and a flashing cursor. I updated the entire system with no success, and scoured google for fixes without finding any that worked. After trying all the switches for shutting down and rebooting the machine, I found halting it to be the one that works. 

Keep in mind this is hardly a fix, but it gets the job done. To avoid this freeze on reboot, use:

```
reboot -f
```

If you are using ssh, you won't get confirmation that reboot has been successful until linux boots back up.

Not the cleanest fix, but it's working fine for me, hope this helps someone.

---

