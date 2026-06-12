---
title: "Kubuntu network card not stating at boot / no gateway"
date: 2005-08-01
forum: Desktop Environments
---

### Post by slumption on 2005-08-01
I set my IP as a static address and added a default route. I've checked the /etc/network/inferaces and my settings are there. As soon as I reboot my NIC doesn't come up and I have to manually set the IP / GW with ifconfig. Same problem if I stick with DHCP. How can I fix this?

I moved from Ubuntu to Kubunutu as Ubuntu freezes after about five mins of use! Hardware is ASUS K8V board, AMD64 Cpu (754 socket), 512ddr, 1 x 80GB IDE drive wtih swap, / and /boot, 2 x 200GB IDE drives RAID 1 (MDADM raid), bog standard DVD drive, onboard NIC, NVIDIA 128MB gcard. I have tried 3 seperate NICS just to check that its not the hardware.

---

### Post by Takis on 2005-08-02
Could you please post the contents of /etc/network/interfaces? You may be missing an 'auto eth0' line or something. A mini-diagram of your network setup you're trying to achieve and what's actually coming up'd be useful too if possible.

As for the default gateway bit, I had to create a service that runs during boot to set that up.

---

### Post by slumption on 2005-08-06
[QUOTE=Takis]Could you please post the contents of /etc/network/interfaces? You may be missing an 'auto eth0' line or something. A mini-diagram of your network setup you're trying to achieve and what's actually coming up'd be useful too if possible.

As for the default gateway bit, I had to create a service that runs during boot to set that up.[/QUOTE]
 All sorted:

The board I was using was based on the Nvidia Nforce chipset. It kept crashing with ubunt and kubuntu I'd loose my network settings.

I put a different baord in reinstalled ubuntu used apt to get kubuntu desktop and I've had no more netowrk problems.

---

### Post by Takis on 2005-08-07
What was wrong with the nForce (I have one too!)?

---

