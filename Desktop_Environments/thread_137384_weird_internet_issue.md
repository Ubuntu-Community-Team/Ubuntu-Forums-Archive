---
title: "weird internet issue"
date: 2006-02-27
forum: Desktop Environments
---

### Post by helmet on 2006-02-27
my nework was working fine. then i tried to change the names of my computers i did it on the windows machine and restarted no problem. went into samba config and changed the appropriate boxes. now my linux box doesn't see past my linksys wrt54gp2 router. i didn't change anything in the router settings or anything else on any machines. i can still talk between them and share files but firefox, ssh, ping all that stuff doesn't go outside my router. they are setup as static ip.

let me know what other info you need to help me out

---

### Post by gingermark on 2006-02-28
I take it you don't have a firewall installed?

Ok I'm gonna hava a guess, without really knowing what I'm talking about. Mainly cos nobody else has answered so far. I'll probably be way off the mark.

If you have changed the name of your machine, does that mean the machine's domain has changed? I mean if you open Konsole does it say username@domain2 where before it said username@domain1 ?

If so, and I stress this is probably wrong, go K-Menu --> System Settings --> Network Settings.

You'll need to activate Admin mode, then click on the domain name system tab. Is there an alias for localhost that includes your systems domain name? If so, if it is the old one, I'd suggest changing it to the new one.

May I stress one more time I don't really know what the hell I'm talking about - but I'd try that if it was my system. Good luck!

---

### Post by retsaw on 2006-03-04
If you haven't sorted this out already, type in "route" and see if the IP for your default gateway matches that of your router.  Or you can check by going in to "Network Settings" and having a look at the "Routes" page.

---

