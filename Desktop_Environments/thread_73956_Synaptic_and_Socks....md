---
title: "Synaptic and Socks..."
date: 2005-10-10
forum: Desktop Environments
---

### Post by cwestpha on 2005-10-10
From college I use a SSH2 tunnle to secure my information to my PC at home. However Synaptic and apt does not like SOCKS. Any way I can get my packages to update and reload the source lists through this tunnle?

---

### Post by KingBahamut on 2005-10-10
Are you trying to tunnel your updates from your Home machine to your college box? for what main purpose?

---

### Post by cwestpha on 2005-10-10
yes.
to bypass a firewall and proxy. Besides I take hacking classes (aka information security) and I encrypt everything in that lab because if it isnt encrypted its fair game to be the class' next lession on breaking apart packets.

---

### Post by KingBahamut on 2005-10-10
You sound as paranoid as me at times. tcpdump can find anything....I know this. 

VPN to external server using pptpd?

---

### Post by cwestpha on 2005-10-10
I am not paranoid. I just use it to bypass the firewall restrictions and make it so intercepting and peicing togeather my IMing with my girl freind doesnt become the next classroom lab.
Seriusly this is most of the class. You learn how to protect things and then how to break the protection. Its literaly a hacking class and any network activity on the classroom's network is fair game for an example or class activity.

I would use a VPN, but they are a bit complicated, easier to detect (I have SSH running on the HTTPS port so it looks like a bunch of secure HTTP trafic), and I dont want to reconfigure a bunch of firewalls.
I dont use SSH2 tunnles like this normaly but when you are on a network that ya have to use and its been set up with the intention of harvesting everyday trafic as examples... you do everything you can to secure it.

---

