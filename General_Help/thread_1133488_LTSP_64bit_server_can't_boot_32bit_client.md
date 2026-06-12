---
title: "LTSP 64bit server can't boot 32bit client"
date: 2009-04-23
forum: General Help
---

### Post by souled on 2009-04-23
I have a server running 64 bit 8.04 set up for LTSP. When I build the client image with --arch i386, the clients won't boot. I disabled splash and quiet boot, and I discovered that it hangs after IP config. It shows the IP, gateway, etc. (this is after PXEboot) and the rootpath and filename that it's trying to boot from, but then it hangs at Negotiation. I think this is when nbdroot is mounted, but I'm not exactly sure. This is before any login is available. The other screens F2-F7 show a blinking cursor.

In the logs, nbdserverd recognizes the connection and serves the image, but ldminfod is never started.  I am however able to boot the clients with the 64bit image just fine. 

I also have a separate 32bit LTSP test server, that works fine. I can even point the SERVER parameter in lts.conf to the 64bit server, and they can connect to that server with no problem.

Thanks

---

### Post by makrem on 2012-02-28
hello 
how can I do to run 32 bit Client on a 64 bit server?
The approach Please , i need it urgent

---

### Post by mörgæs on 2012-02-28
8.04 is an old version. Thread closed.

---

