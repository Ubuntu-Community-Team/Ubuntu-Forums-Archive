---
title: "Memory upgrade help"
date: 2010-01-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by leehach on 2010-01-22
Trying to add memory to my Inspiron 530s. According to the docs, it can take 2GB in each slot. According to the user manual, paired slots (1/3 and 2/4) do not have to both be filled, but if they are both filled they should be at the same speed / same technology. 

Slots 1/3 are filled with the factory installed two 1GB 667MHz DIMMS. I added one 2GB 800MHz DIMM to slot 2 and nothing in slot 4. Again, according to the manual it should be kosher. I installed the DIMM, machine booted up fine, rebooted several times over the course of the week, and then suddenly the machine locks up, have to do a hard reboot, and it won't get past the BIOS*splash screen--i.e. no grub, no booting from a rescue disc or recovery partition, nothing. So I pull the new 2GB DIMM and the machine starts fine. I swap out the old memory and try *just* the new DIMM, no dice. So now I'm running with just the old DIMMs.

So the question is, is this just bad luck, i.e. memory just flakes sometimes? Or could this be caused by mixing memory speeds, or not filling in both slots (2/4), or something else? It seems from poking around on the web that I am not the first one to have done this, and others have had success.

---

### Post by myth1914 on 2010-01-22
It sounds like you need to turn off dual channel within the bios.  I don't know what would happen if you only have 1 slot filled and dual channel on...  Perhaps it fried the memory you installed.  Either way, it's worth a try.

---

### Post by pricetech on 2010-01-22
They should always be installed in matched pairs.

You won't gain any speed with faster RAM, it will run at the speed of the existing 667 RAM.

You could just have a defective stick of RAM.  Return it for exchange and buy a second one while you're there.

---

### Post by leehach on 2010-01-22
Thanks guys. I went back to the docs, and I think I misunderstood what it said:
> DIMM connectors must be populated in numerical order beginning with
connectors DIMM_1 and DIMM_3, then connectors DIMM_2 and DIMM_4.
If a single DIMM is installed, you must install it in connector DIMM_1.
I took that last sentence ("If a single DIMM is installed…") to mean that the DIMMs don't have to be in matched pairs, but looking back at it, it means you can have 1, 2, or 4 DIMMs installed but not 3. 

Thanks for the replies, myth1914 and pricetech!

---

