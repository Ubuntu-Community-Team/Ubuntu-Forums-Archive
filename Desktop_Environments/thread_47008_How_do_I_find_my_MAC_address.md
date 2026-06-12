---
title: "How do I find my MAC address?"
date: 2005-07-06
forum: Desktop Environments
---

### Post by spiffytech on 2005-07-06
My firewall is set to allow specified MAC addresses through, and I need to find my kubuntu address to get access to the net. How do I do this?

---

### Post by tread on 2005-07-06
Type ifconfig in a terminal.
The address after HWAddr is the one you want.

Alternately, right click on the wireless network status applet, click properties->support. The address after Network Device is the one.

---

### Post by maulattu on 2005-07-11
[QUOTE=tread]Type ifconfig in a terminal.
The address after HWAddr is the one you want.

Alternately, right click on the wireless network status applet, click properties->support. The address after Network Device is the one.[/QUOTE]
 or, if it doesn't work, try this
*sudo ifconfig*
:D

---

