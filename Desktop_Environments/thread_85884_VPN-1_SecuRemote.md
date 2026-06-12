---
title: "VPN-1 SecuRemote"
date: 2005-11-03
forum: Desktop Environments
---

### Post by VR6Pete on 2005-11-03
Are there any Linux alternatives to VPN-1 SecuRemote for Ubuntu? 

I'm having difficulty finding a product that will allow me to connect in via a checkpoint VPN gateway.

Thanks,

Pete

---

### Post by markr on 2005-11-04
I'm having the same problem,  if anyone knows of a way to connect via Linux, I'd like to know.

Mark.

---

### Post by beow on 2005-11-05
Agree. Think this is _the_ major obstacle preventing a transition from windoz to Ubuntu at many work laptops. While there are tools for connecting to the home (i.e. static connections) using ssh with reverse port forwarding and vnc etc, connections to the companys VPN must work on the road also. This should have a high priority.

---

### Post by VR6Pete on 2005-11-05
Agreed.

---

### Post by markr on 2005-11-07
I've been thinking,  has anyone tried to installed the VPN-1 SecureClient via wine?  Don't know much about network and low level stuff like that, but I'm thinking of two options:

1. Installl the Secure Client via Wine and see if I can get it working.
2. Install vmware and try and get a connection through the guest XP os.

I'll be giving it a try over the next week or so and will let you know how I get on,  in the meantime, if anyone has already tried this, please let me know!!

Mark.

---

### Post by VR6Pete on 2005-11-07
I tried wine, and Xover office, but no go.... bombs out during installation. Which i suspected that would happen.

---

### Post by Novack on 2005-11-17
I have the same problem. I know that at least in certain circumstances Openswan can be used to connect to CheckPoint VPN gateway.

[http://wiki.openswan.org/index.php/interoperatingCheckpoint](http://wiki.openswan.org/index.php/interoperatingCheckpoint)

This is not a very high priority for me (would be nice though!) so I haven't delved too deep into it. If someone gets this to work, please post a how-to here!

---

### Post by doogle on 2005-11-18
Just stumbled across this now.  Would be very interested in a solution.  Especially as I could then get some sort of VNC working to my work computer and not have to set up many development environments.

---

### Post by rverrips on 2005-11-20
Hi 

This thread has been going round couple times ...

Sadly to date no SecuRemote client, but if you read here there's one way to do it (requires a windows host on your network though)

[http://www.ubuntuforums.org/showthread.php?t=21105&highlight=checkpoint](http://www.ubuntuforums.org/showthread.php?t=21105&highlight=checkpoint)

Yours

Roy
:(

---

### Post by senectus on 2005-11-21
just for the sake of taking a tally.. I'd like this as well (plus netscreen VPN too)

---

### Post by cestes on 2006-07-21
Bump on this issue.

talking to Checkpoint is the last thing keeping me from wiping the HD on my work laptop and starting over!

---

### Post by jinxed on 2006-08-07
I could use this functionality, too. This is one major issue in my complete conversion from Windows to Linux.

---

### Post by DooMRunneR on 2006-09-22
It´s also a major issue for me, as it-company we make much remote-administration through netscreenfirewalls, so a vpn-client with netscreen-policy-import would be nice :)

---

### Post by jackthomas on 2006-09-22
Another 'me to', does anyone know of a good guide to getting openswan working on Ubuntu?

---

### Post by Megapearl on 2006-10-09
I'm searching for the same answer, i need to connect to my work's intranet, they are using a netscreen vpn router, and the only client i can find is a windows client called 'NetScreen-Remote' it is using Phase 1 Aggressive Negotiation Mode, i can't find any good client or howto for configuring it under ubuntu, it would be nice having a linux client where i can just import the netscreen policy...
Any help would be greatly appreciated.

Regards,
Donald Flissinger.

---

