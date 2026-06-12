---
title: "firestarter and samba"
date: 2006-02-21
forum: Desktop Environments
---

### Post by cskeide on 2006-02-21
I just did a fresh install of ubuntu, and I am having some trouble browsing the local windows network. I have added a policy to allow incoming SMB connections from everyone. And yes, it all works fine when I disable firestarter.

I had the same problem before formating and re-installing ubuntu, but then I was able to solve it by "allowing broadcast" in firestarter's preferences menu. This time, however, that solution does not work.

firestarter's "Events" tab keep displaying blocked "Sun-RPC portmap". I tried to add a policy for the incoming port, but it seems like the port number is random...! I never saw these errors before, and I am pretty confident that I didn't allow incoming rpc-connections the previous time I encountered this problem.

Any ideas?

Thanks,
Chris

---

### Post by cskeide on 2006-02-22
Anyone?

---

### Post by kaamos on 2006-02-22
Have you opened the ports 137-139 and 445 ?

---

### Post by cskeide on 2006-02-22
[QUOTE=kaamos]Have you opened the ports 137-139 and 445 ?[/QUOTE]

Yes, I have. And it all works fine if I type smb://192.168.0.x in the run dialog. But it seems like firestarter blocks name resolving. And that the Sun-RPC ports is used for this? Doesn't make sense to me. But I guess... the Windows Network never did.

---

### Post by kaamos on 2006-02-22
Well, I'm with you on the last part. :roll: 

This is a total shot in the dark, but open up port 53 as well as that deals with dns.

---

### Post by cskeide on 2006-02-22
Tried that. Didn't work.

Here's the event's list for one attempt to access the windoze box (192.168.0.2) (funny thing is, both the win boxes seem to reply?):

```

Port:32934 Source:192.168.0.3 Destination:192.168.0.98 Protocol:UDP Service:Unknown
Port:32935 Source:192.168.0.2 Destination:192.168.0.98 Protocol:UDP Service:Unknown

```

EDIT: Oh, and yeah... Today it says service: unknown. Yesterday it said Sun-RPC portmap. Weird.

---

### Post by cskeide on 2006-04-18
Thought I'd just post my solution to this problem.

Since I was able to connect to my windows computers by entering smb://ip-address in the run dialog, it was pretty obvious that firestarter blocked name resolving in some way.

In order to fix this problem I configured my router so that my computers are given the same ip address every time a dhcp lease is requested. This way I could just add my windows computers to the /etc/hosts file on my ubuntu box.

```

192.168.0.2   windows1
192.168.0.3   windows2

```

Now, I am able to enter smb://windows1 or smb://windows2 in the run dialog, and everything works fine.

Still not able not browse the windows network through "Places > Network Servers" though. :(

---

