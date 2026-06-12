---
title: "GX270 Advice"
date: 2007-09-09
forum: Dell  Ubuntu Support
---

### Post by hey_ygbsm on 2007-09-09
Considering buying a refurbished GX270 or SX270 budget linux box for my daughter.  Was wondering if anyone has had good success with a Fesity install on one of these.  If so, are there any issues I need to be aware of?  Or, perhaps there's a better budget, small form factor platform I should consider?

---

### Post by Daveski on 2007-09-09
> **hey_ygbsm said:**
> Considering buying a refurbished GX270 or SX270 budget linux box for my daughter.

Some GX270 motherboards die after 2-3 years with leaking capacitors. I don't know if this also affects the SX270 boards.

Symptoms are usually power related, such as the machine spontanteously powers off or enters a sort of power-saving mode from which it cannot be woken.

I love the Optiplex range, but I would warn people about the flaw in some GX270's.

---

### Post by hey_ygbsm on 2007-09-14
Thanks Daveski.  Aside from the blown caps, this is an Ubuntu-friendly config, huh?  No ATI video lurking inside?

---

### Post by Daveski on 2007-09-17
GX270 Small MiniTower with the built-in Intel video and Intel Pro NIC seem to work just fine with Feisty. Sound, network and video all right from the liveCD - although I do not have one which has an installed and fully up-to-date OS.

---

### Post by andrew.46 on 2007-10-01
Hi,

 I have a GX270 and it appears to love Ubuntu :-) It ran Dapper for a long time and is now running Gutsy Beta with no problems.

 Only 2 small bits of advice:

[LIST=1]
[*]You will need to increase video memory allocation in the bios from 1 to 8
[*]I upgraded to 1024 ram, it was cheap and made a _huge_ difference.
[/LIST]

           Andrew

---

### Post by Lil on 2007-10-01
I've been using Ubuntu on a GX240 which has some issues with power management (it won't sleep or hibernate) but it's been a trooper and everything worked out of the box bar the latter two issues I've mentioned.

The GX260 and 270 have also worked just great and if anything I would recommend the GX260 as whilst it might come with a lower spec', it's less susceptible to the leaking capacitor issue and it can take decent CPU upgrades (it supports a 533MHz front side bus based P4) and is based on DDR RAM like the GX270.

Personally my GX240 on Feisty has been a real trooper despite the whole system only setting me back £60, and it runs very well indeed on a P4 2.4GHz, 512MB, GeForce 5200FX etc.

Vicky

---

### Post by ChuckL on 2007-10-16
I have a GX270 running Ubuntu 7.04 for quite some time now. So far I have had only two issues. 

I had to add a new video card in order to get my Dell 2007FWP wide screen LCD monitor to work. I kept getting blue screens whenever X attempted to load. While I most likely could have found an updated driver for the onboard video, I opted for a better and faster video card. If you have a standard monitor this should not be a problem for you.

I recently attempted to upgrade my memory to 4GB but have been unable to do so because of the limitations with 32-bit Linux. I have for the moment backed my memory down to 3GB and have had no problems. I am going to probably attempt to load the 64-bit version of Ubuntu as soon as I get a chance since the Intel Core 2 Duo CPU is a 64-bit processor. That should allow me to max out my memory.

By the way, my GX270 is a refurb'd machine and works great. I love it.

Regards,

Chuck

---

### Post by Nick Payne on 2007-10-16
I have had Ubuntu running on a GX270 for a couple of years. Mine has an nVidia video card in it. Presently running Gutsy beta with the full compiz effects enabled...

---

### Post by hey_ygbsm on 2008-01-06
Thanks all!  I ended up getting an ESC AM2 mobo with onboard Nvidia instead.  Works like a champ.  I may still purchase a budget GX270 system if I see a price I can't refuse.

---

