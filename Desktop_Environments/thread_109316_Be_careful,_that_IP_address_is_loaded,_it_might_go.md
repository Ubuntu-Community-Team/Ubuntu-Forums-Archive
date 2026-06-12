---
title: "Be careful, that IP address is loaded, it might go off!"
date: 2005-12-28
forum: Desktop Environments
---

### Post by ddesmarais58 on 2005-12-28
For some unknown reason, when I installed my Kubuntu on my laptop, I gave my system a fixed IP address of 192.168.10.4. Why? I don't know what possessed me. (I took my tinfoil hat off and the alien radio waves got to me.)

1) Will this hurt me in the long run?
2) How to fix it without sending my system into never-never-land?

I guess I thought I had to choose something different from my router at 192.168.10.1.  There are not many pc's on my home network and they get their IP addresses by DHCP. I am concerned that when I return to my office, where many machines share one internet connection, there will be an address conflict and that I am otherwise blithely walking into disaster.

This situation came to my attention when Webmin denied me access at the 192.168.10.1 address. I know that I can tell Webmin to allow that address, if necessary, but I am concerned about the larger implications.

My /etc/hosts file contains this address as does /etc/network/interfaces - perhaps other files.

Opinions? Help? Thanks in advance!

---

### Post by cwaldbieser on 2005-12-28
[QUOTE=ddesmarais58]For some unknown reason, when I installed my Kubuntu on my laptop, I gave my system a fixed IP address of 192.168.10.4. Why? I don't know what possessed me. (I took my tinfoil hat off and the alien radio waves got to me.)

1) Will this hurt me in the long run?
2) How to fix it without sending my system into never-never-land?

I guess I thought I had to choose something different from my router at 192.168.10.1.  There are not many pc's on my home network and they get their IP addresses by DHCP. I am concerned that when I return to my office, where many machines share one internet connection, there will be an address conflict and that I am otherwise blithely walking into disaster.

This situation came to my attention when Webmin denied me access at the 192.168.10.1 address. I know that I can tell Webmin to allow that address, if necessary, but I am concerned about the larger implications.

My /etc/hosts file contains this address as does /etc/network/interfaces - perhaps other files.

Opinions? Help? Thanks in advance![/QUOTE]

You can probably just go into System -> Administration -> Networking, select your network card, click on Properties -> Connection Settings Configuration -> and set it to use DHCP.  Your card should get it's IP address from your router.

---

### Post by ddesmarais58 on 2005-12-29
Thanks.

I made the change and did not experience any negative effects.  Thanks a lot.

---

