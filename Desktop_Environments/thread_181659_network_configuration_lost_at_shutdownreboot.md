---
title: "network configuration lost at shutdown/reboot"
date: 2006-05-24
forum: Desktop Environments
---

### Post by equaeghe on 2006-05-24
Hi,

I recently helped a friend with a Ubuntu 5.10 install. All went well, but because he uses an adsl modem connected to his computer with a lan cable (i.e., pppoe), the network was not configured during the initial install. The network card is detected, and it is possible to manually initiate an internet connection using the following steps (possibly su'ing along the way):

1. System ==> administrator ===> network ==> activate Ethernet connection
2. Applications ==> accessories ==> terminal ==> pon dsl-provider (gives "plugin rp-pppoe.so loaded" as a result)

At this point the network is perfectly working. I remember doing a config for pppoe to make it stick, and the normal network settings also seem to be saved correctly.

When shutting down, the only failure we get is:

deconfiguring network interfaces   [fail]

This made me somewhat suspicious already.

At boot time, we get a "synchronizing clock failed" message, indicating something was wrong with the internet connecting (what step? setting up eth0 or pppoe?).

This was indeed the case. Manually bringing the network up as described before worked, it was clear eth0 was down and the problem was at this stage. After uselessly trying (mainly changing details in the network administration gui) I called quits for the day. Afterwards he sent me his '/etc/network/interfaces', which I hoped would point the problem out and lead to a solution. I am apparently not familiar enough with the innards of ubuntu/debian, however. I'll include it in attachment of the post for reference.

Can anybody help me making the network configuration stick? Thanks in advance for your help.

Erik

---

### Post by Hentai_Jeff on 2006-05-25
sounds like he's not saving sessions, give that a try.

---

### Post by equaeghe on 2006-05-25
[QUOTE=Hentai_Jeff]sounds like he's not saving sessions, give that a try.[/QUOTE]

Thanks for replying, Jeff. 

Could you be more specific on what you mean with "saving sessions"? I don't have an Ubuntu install at hands, so I can't look around. What menu or configuration gui should I go to or what command should I type? (I didn't find anything informative by googling for 'ubuntu "(not) saving session(s)".)

Erik

---

