---
title: "Screen freezes on logout"
date: 2008-07-25
forum: Desktop Environments
---

### Post by tigernerd on 2008-07-25
Hi,

I am running an old Dell computer on Hardy with 512 mb of memory and an unknown processor. I upgraded the video card from an ancient Ati rage 128 to a old Radeon 9600 card, haven't got the fglrx driver to work, but the "ati" driver appears to work fine. (The computer, in short, sucks, and needs a new motherboard, processor, and more memory, and possibly more hard drive space.)

Now, whenever a user logs out twice without rebooting, the screen locks up. I can't escape to a login shell, and the only option is to press that reset button. /var/log/messages is not very enlightening.

Would it help if I set X to restart on logout, and how do I do that? (I'm used to Red Hat systems, on which X restarts on logout by default)

---

### Post by tigernerd on 2008-07-26
I hate to bump, but seriously, this is getting on my nerves.

---

### Post by zen101252 on 2008-08-03
> **tigernerd said:**
> Hi,

I am running an old Dell computer on Hardy with 512 mb of memory and an unknown processor. I upgraded the video card from an ancient Ati rage 128 to a old Radeon 9600 card, haven't got the fglrx driver to work, but the "ati" driver appears to work fine. (The computer, in short, sucks, and needs a new motherboard, processor, and more memory, and possibly more hard drive space.)

Now, whenever a user logs out twice without rebooting, the screen locks up. I can't escape to a login shell, and the only option is to press that reset button. /var/log/messages is not very enlightening.

Would it help if I set X to restart on logout, and how do I do that? (I'm used to Red Hat systems, on which X restarts on logout by default)



I have had problems with the screen freezing when I click on the log off button. When I switched from compiz to metacity it worked. I also have unticked loose binding and indirect rendering for compiz which seems to have an effect. ( I use the compiz-fusion button which you can install from synaptic.)

Tim

---

### Post by jelofson on 2008-08-19
I have logout freeze problems with my ati card when using the restricted driver. When I click logout, it hangs completely and I can't restart x or get to a terminal. I have to hold down the power button. It doesn't matter if compiz is enabled or not. With the opensource driver, it works, but no 3d. I haven't found any solution yet.

---

