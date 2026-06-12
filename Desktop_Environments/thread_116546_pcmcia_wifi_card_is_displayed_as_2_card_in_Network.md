---
title: "pcmcia wifi card is displayed as 2 card in Networking"
date: 2006-01-12
forum: Desktop Environments
---

### Post by disk0bug on 2006-01-12
When I use my old Cisco wireless card, it is well recognize.  But when I go in the Networking configuration (System - Networking), I see 2 card called Wireless Connection.  They are eth1 and eth2.  eth1 is active and eth2 is innactive ... and it doesn't work.

To activate my wireless connection, I need to deactivate eth1 and activate eth2.

I need to do that everytime I boot...  How can I fix that?  :confused: 

Thx

---

### Post by marcw on 2006-01-14
I have the exact same problem, possible with the same card.  You didn't state the model; mine is the 350.

I made one change though, I eliminated all references to eth1 in my /etc/network/interfaces file.  The only thing in there now is eth2.  But it still refuses to start after a boot.  I have to do the same as you.

I'd also like an anser to this, if one exists.

---

### Post by disk0bug on 2006-01-16
My card is a Cisco 340 serie

Anyone have an idea how to fix that?

:confused:

---

