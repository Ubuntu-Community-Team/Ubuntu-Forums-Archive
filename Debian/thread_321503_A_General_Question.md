---
title: "A General Question"
date: 2006-12-19
forum: Debian
---

### Post by steven8 on 2006-12-19
Howdy,

I mentioned this in the DreamLinux thread and SlimDog wasn't sure why, so I thought I'd throw it out for ideas.  I have tried the dreamlinux distro, and find it to be quite nice.  Except for one issue.  My modem, a usb cable modem, works just great with the livecd.  That is why I installed the OS an a partition.

Anyway, now that it is installed, my modem doesn't work.  And this is where it gets funny. . .When the OS begins to load, the modem shows activity.  Then, when the OS gets to the end of loading, the modem stops working.  It's as though someone put in some kind of script to shut of the module which runs my modem.  It uses rndis_host, and thsi is present under the liveCD as shown with lsmod.

I haven't had a chance yet to look in the actual installed version, but my question is not how to find out if the driver has been loaded, but does anyone know of what may have been done to cause it to 'unload' at the end of booting?

---

### Post by ardvark71 on 2006-12-21
> **steven8 said:**
> Howdy,

I mentioned this in the DreamLinux thread and SlimDog wasn't sure why, so I thought I'd throw it out for ideas.  I have tried the dreamlinux distro, and find it to be quite nice.  Except for one issue.  My modem, a usb cable modem, works just great with the livecd.  That is why I installed the OS an a partition.

Anyway, now that it is installed, my modem doesn't work.  And this is where it gets funny. . .When the OS begins to load, the modem shows activity.  Then, when the OS gets to the end of loading, the modem stops working.  It's as though someone put in some kind of script to shut of the module which runs my modem.  It uses rndis_host, and thsi is present under the liveCD as shown with lsmod.

I haven't had a chance yet to look in the actual installed version, but my question is not how to find out if the driver has been loaded, but does anyone know of what may have been done to cause it to 'unload' at the end of booting?

Hi,

Is it possible to route your connection through a LAN port? I've never had much luck with getting high speed USB connections to work well (or work at all.) 

Best Regards...

---

### Post by steven8 on 2006-12-22
Well, the usb modem is really my only option.  I have no space left in my computer for a lan card.  Dapper (ubuntu and kubuntu), gNewSense both work with it right out the gate.  No configuring at all.  DreamLinux is weird now.  Even though I have pc and data activity on the modem, it doesn't find a connection when I try to browse.  I gave up on DreamLInux, even though I like it very much.

Edgy and Feisty do not see my modem either. :-(

---

### Post by mips on 2006-12-22
> **steven8 said:**
> Well, the usb modem is really my only option.  I have no space left in my computer for a lan card.  Dapper (ubuntu and kubuntu), gNewSense both work with it right out the gate. 

Compare the relevant config files, you should be able to carry them over from ubuntu to dreamlinux seeing they are both debian based.

Just don't ask me which config files as I dont know ;)

---

### Post by steven8 on 2006-12-23
I can do that?  Then I should able to use the same config files from Dapper to Edgy?  My modem won't work in Edgy, either.

---

### Post by mips on 2006-12-23
> **steven8 said:**
> I can do that?  Then I should able to use the same config files from Dapper to Edgy?  My modem won't work in Edgy, either.

Besides config it could also be a module/driver issue.

---

### Post by steven8 on 2006-12-23
It must be config, because the same driver is present in Edgy, but it doesn't get assigned to my modem.

---

### Post by mips on 2006-12-24
> **steven8 said:**
> It must be config, because the same driver is present in Edgy, but it doesn't get assigned to my modem.

There might be version number differences. You wont know until you ty.

---

