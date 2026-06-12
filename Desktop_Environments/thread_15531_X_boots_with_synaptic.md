---
title: "X boots with synaptic ?"
date: 2005-02-15
forum: Desktop Environments
---

### Post by jamaas on 2005-02-15
Can anyone tell me how to clear up a couple of problems.  When Ubuntu boots into X, it comes up with the password request for synaptic, which I have to cancel out of before proceeding .... no idea why, might have had to do a shutdown in the middle of synaptic use at some point previously.

Also Ubuntu does not boot directly to X, just to a login prompt and then once I login I can startx.  I don't seem to have a menu choice anywhere to change it to allow it to boot right to X.

What have I screwed up this time and how can I fix these?

Thanks a bunch

Jim

---

### Post by lao_V on 2005-02-15
I have experienced a similar issue whereby if I logout it sometimes takes me to text based login prompt instead of the GDM. Haven't figured out when and why it does it yet.
 
 Maybe cuz I'm using Hoary development?

---

### Post by ubuntu_fan on 2005-02-15
[QUOTE=jamaas]Can anyone tell me how to clear up a couple of problems.  When Ubuntu boots into X, it comes up with the password request for synaptic, which I have to cancel out of before proceeding .... no idea why, might have had to do a shutdown in the middle of synaptic use at some point previously.

Also Ubuntu does not boot directly to X, just to a login prompt and then once I login I can startx.  I don't seem to have a menu choice anywhere to change it to allow it to boot right to X.

What have I screwed up this time and how can I fix these?

Thanks a bunch

Jim[/QUOTE]

jamaas,

For the first question about Syaptic: this is totally normal behaviour. The prompt for your password is due to having to run Synaptic as a more priveledged account (root).

As for your GDM: This can be due to your runlevel being incorrectly set in /etc/inittab. Edit the line saying "id:2:initdefault:" to make it read "id:3:initdefault:". Save and reboot. Shoudl fix the problem!

a.

---

