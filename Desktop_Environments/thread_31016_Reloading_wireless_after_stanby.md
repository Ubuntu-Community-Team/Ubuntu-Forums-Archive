---
title: "Reloading wireless after stanby"
date: 2005-05-01
forum: Desktop Environments
---

### Post by brokenflea on 2005-05-01
i just finished setting up kubuntu on my notebook (ibm thinkpad i1300) , everything's working fine except that when i put my notebook into suspend mode and bring it back my wireless networking's not working. i'm using a pc card for the wireless connection (netgear wg511v2), i've tried running /etc/init.d/networking restart but that doesn't help. is there a different approach i need to take to get wlan up and running. any advice would be gladly appreciated. 

TIA

---

### Post by govert on 2005-05-06
[QUOTE=brokenflea]i just finished setting up kubuntu on my notebook (ibm thinkpad i1300) , everything's working fine except that when i put my notebook into suspend mode and bring it back my wireless networking's not working. i'm using a pc card for the wireless connection (netgear wg511v2), i've tried running /etc/init.d/networking restart but that doesn't help. is there a different approach i need to take to get wlan up and running. any advice would be gladly appreciated. 

TIA[/QUOTE]

Try to unload , and reload the network module before restarting the network:

% rmmod [module]
% modprobe [module]
% /etc/init.d/networking restart

[module] is probably something like "netgear" or " wg511v2"
use the command lsmod  to see all the currently loaded modules.

I haven't tested this, but similar remedies have been suggested for similar problems in similar threads... :-)

---

### Post by az on 2005-05-06
In /etc/networking/if-pre-up and /if-post-down you can put scripts which do things just before the link goes down and once it comes back up.

In /etc/apm there is a simlilar stucture for such things (events).  You will need to do this with acpi, but since I do not use that, all I could say is that I would assume that it should work the same way. (/etc/acpi)

You should look to see if this was reported as a bug (which it should be)

bugzilla.ubuntu.com

If you cannot find one, please file one and follow up on it...

---

