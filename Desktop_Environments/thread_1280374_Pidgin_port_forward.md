---
title: "Pidgin port forward?"
date: 2009-10-02
forum: Desktop Environments
---

### Post by jakerue on 2009-10-02
Hi, recently installed a linksys 54G and my pidgin can no longer connect to any irc.  I have searched all over for a solution but nothing.  Do I need to forward some ports onward?  Which ones?  


The lack of other people having this problem also confuses me...what exactly is happening here?

Thanks in advance,

Jason

---

### Post by undecim on 2009-10-02
No, port forwarding only needs to be done when an outside address needs to start the connection. For example, I have ports forwarded on my routers that allow me to connect to my home server while I'm at my university. Connecting to an IRC server, the connection starts from your computer.

It may be a security feature of the router. Some viruses use IRC to connect back to a controller for instructions, so check that IRC or the IRC ports (192 and 6667 i believe) aren't blocked. (Look around in the "security" tab.)

---

### Post by jakerue on 2009-10-04
Thanks for the reply.  I've opened those ports and still a perpetual 'connecting'.  I have a similar linksys router at home (160N) and have no problems.  I am on a school-based LAN here so maybe something has changed there instead of on my machine.

To make this easier do you know any other places I could check?

---

### Post by undecim on 2009-10-04
You shouldn't be opening any ports. You only need to open ports if you are running an IRC server, but you just want the client.

If it's on school connection, they are probably blocking those ports. Could you be a little more specific about what happens when you try to connect? what error text do you get?

---

