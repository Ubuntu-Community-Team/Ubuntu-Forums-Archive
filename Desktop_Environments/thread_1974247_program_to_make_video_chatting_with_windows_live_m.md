---
title: "program to make video chatting with windows live messenger"
date: 2012-05-05
forum: Desktop Environments
---

### Post by forsubhi on 2012-05-05
I need program work on kubuntu 11.10 to make video chat with persons who use windows live messenger on windows .

---

### Post by Zorael on 2012-05-06
I'm not sure there is any client that can do this anymore. Supposedly Microsoft used a central SIP server for video calls, until at some point in 2009 (or early 2010?) when they released a mandatory update that changed this to a very proprietary and closed-down peer-to-peer system. Eventually in early 2010 they shut down the SIP servers completely, locking out everyone not using their official client.

Quoth [aMSN development team March 2010](http://kakaroto.homelinux.net/2010/03/amsn-0-98-2-to-be-released-without-audiovideo-support/);
> We (the aMSN team) want to soon release aMSN version 0.98.2 because of the various issues we faced with 0.98.1 because Microsoft changed their protocols.. mainly the problem with the nickname changing to the email at every connection.

We also recently realized that the Audio/Video capability would need to be dropped because it just doesn’t work anymore unfortunately :(

Microsoft forced everyone to upgrade to the latest version of Windows Live Messenger : WLM 2009 which uses MSNP18 and has the ability to do Audio/Video calls through a tunneled SIP (P2P SIP messages, not using an external SIP server) and so, they realized that their SIP servers aren’t being used anymore, so they had this great idea of shutting down their servers… the result? aMSN can’t do Audio/Video calls because the SIP server refuses our connections.

Now we have two choices, either use MSNP18, or disable SIP calls completely. Obviously, we can’t move to MSNP18 at the moment, because MPOP support isn’t really ready yet, and because MSNP2PV2 hasn’t been implemented, so we had to remove the Audio/Video support in aMSN SVN for now, and only have it available for those who are brave enough to try out MSNP18.

We will soon release 0.98.2 as it is long overdue now, and we want to let people know why their A/V calls are not available to them anymore.

I hope everybody will understand why this is happening and we won’t get flooded by n00b questions everyday…

Cursory googling of 'linux msn p2pv2' shows that the Telepathy crew may have gotten it to work. I'm not sure though as I can't really get it to work myself.

---

### Post by tomatoe on 2012-05-06
You can chat with different messaging services through empathy. It also has windows live in their list.

---

