---
title: "Cisco VPN and vpnc questions"
date: 2006-06-22
forum: Desktop Environments
---

### Post by Swad on 2006-06-22
After some work, I was finally able to get both of these clients working and even managed to find a fix to get the Cisco VPN client working w/o needing to sudo (it involved a chmod 4111 to the cvpnd file).  With that said--two questions.

1) When you fire up the Cisco VPN client, it keeps the terminal window locked into the client.  Is this normal (I'm not used to Cisco VPN on Linux)?  I can ctrl-c and it disconnects but I'm just wanting to make sure that the terminal window which I run it from is suposed to be locked to it.

2) Is it possible to run vpnc as a regular user w/o sudo?

3) I lied--just thought of a third question.  Is it possible to store the group info for vpnc in a file and keep it encrypted similar to how Cisco VPN does?  It would be idea for me to just have to fire up the software pointing to a profile and only have to enter my user's password, but also w/o my password information being stored ina  config file as plain text.

Thanks for any info.

---

### Post by Swad on 2006-06-23
Friendly bump given this has slipped into high number pages and I also posted this at an aweful time in the morning so it was probably missed by a number of people during the day.

---

