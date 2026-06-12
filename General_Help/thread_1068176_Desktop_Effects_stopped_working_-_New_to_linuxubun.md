---
title: "Desktop Effects stopped working - New to linux/ubuntu"
date: 2009-02-12
forum: General Help
---

### Post by Silvershark2005 on 2009-02-12
okay im new here and to ubuntu as the title says, so please take it easy on me.

But on to the problem. I recently installed Ubuntu 8.10 onto my buddies VAIO Laptop and everything was working great. I attempted to connect the laptop to his big tv as a dual display and i couldnt get it to work. So i just gave up. well ever since i have tried that, ubuntu will not allow me to enable visual effects. 

Also, how do you remove software? i cant seem to find that control.:popcorn:

---

### Post by kestrel1 on 2009-02-12
Have you enabled any proprietary drivers that may be available. To check & see if any are available go to:
System -> Administration -> Hardware Drivers.
Enable any that are there.
To remove software that was installed via Synaptic, just use synaptic again & check the software for removal.

---

### Post by Silvershark2005 on 2009-02-12
yeah i have looked in that hardware driver menu. there isnt anything in there.

---

### Post by Silvershark2005 on 2009-02-13
any ideas?

---

### Post by overdrank on 2009-02-13
> **Silvershark2005 said:**
> any ideas?

Hi and I assume you are using the intel graphics. You may try and reconfigure you xorg with this command in the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x with the ctrl, alt, backspace keys.

---

### Post by Silvershark2005 on 2009-02-17
> **overdrank said:**
> Hi and I assume you are using the intel graphics. You may try and reconfigure you xorg with this command in the terminal ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x with the ctrl, alt, backspace keys.

yeah that worked. 

how can i hook up an external display?

---

