---
title: "temspeak server"
date: 2006-02-22
forum: Desktop Environments
---

### Post by pacificdrums on 2006-02-22
I am running a ts server on a ubuntu box and i got it installed and i have had people connect to it but some times after i do not use it from the wan side for a while it seems like the port gets closed or something. I can still connect on the LAN but that's it. I have the ports forwarded in my router and it is also hooked in to a hub. Could that be a problem? I have been reading around and can not figure this one out. I am thinking it has something to do with ubuntu (although i do not want to) but it is the only thing that i can think of :-k . please help!!	](*,)

---

### Post by pacificdrums on 2006-02-22
Actually dose ubuntu close the ports until something is sent out?? If so how can i make port 8767 UDP stay open all the time?

---

### Post by stevea1210 on 2006-02-22
Does the TS box have a static IP?  If not, DHCP could be the issue.  Connecting from the LAN wouldn't be effected if you connect via unc name and the ip changed.  However from the wan, the router wouldn't forward the port to the proper IP.

Basic question, but want to eliminate it off the bat.

---

### Post by pacificdrums on 2006-02-22
Yes i have the ubuntu box set static but my wan is dhcp but i am using dyndns.com for that. So it is set to forward to the static ip.

---

