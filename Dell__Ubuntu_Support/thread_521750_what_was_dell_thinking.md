---
title: "what was dell thinking"
date: 2007-08-09
forum: Dell  Ubuntu Support
---

### Post by jacob01 on 2007-08-09
i bought a dell e520 n with ubuntu and when i found out it used a usb keyboard it kind of bothered me but then i thought "why would they sell a computer were you cant use it because the keyboard or mouse doest work" but any ways here i am typing to you and thinking wow they expect to sell this to a person who like to use linux who uses another distro. although other distros do have usb keyboard support to my knoledge, what if the one you use or want to try doesn't have usb support.

i ran into this problem when trying to boot from the open suse live cd which you'd think would have pretty good support being another pretty well known and well supported distro.

also dell did not include a ps/2 port like the older computers used

is there a fix or am i the only one

why did they not include an alternative port on a linux computer since usb keyboards are not that old

i tried the distro in a virtual machine and it worked great but a bit slow

you may want to take this into consideration when buying a dell

the only thing i could come up with for why they do that, is adding another port for just the linux computers would cost to much because they would have to use differant motherboads

---

### Post by rfruth on 2007-08-09
If the BIOS supports USB whats the problem ?  My 6+ year old ebay desktop came with a Dell USB keyboard & mouse, Ubuntu (& Kubuntu) saw um both no problem.  :confused:

---

### Post by mike999999 on 2007-08-09
The old ps/2 port is starting to be removed from all systems/motherboards, this really is a legacy port and has been replaced by USB. 

Woohoo, bye bye southbridge.  :)

Just so you know, this has nothing to do with linux or the vendor but more to do with technological progress.

---

### Post by jacob01 on 2007-08-09
yea i figured that but not all distros support usb keyboards well from what i experienced

---

### Post by technikalKP on 2007-08-09
There should be an option like 'USB Legacy Emulation' or something similar in the bios.  Ensure that's enabled and the OS will essentially see the USB keyboard as a PS/2 keyboard.

---

### Post by cstrippie on 2007-08-09
Neither of my last two Dells have had ps/2 ports...or parallel ports for that matter.  Both were laptops, so I don't know if desktops are the same.

---

### Post by bimmerd00d on 2007-08-10
we see this everyday at work when upgrading people's systems.  They like the kb/mouse they have.  I just purchased a handful of the PS/2 to USB adapters and there have been no complaints whatsoever.

---

### Post by jacob01 on 2007-08-10
really the adapters work
does the bios and os recognize the keybnoard as a ps/2 or a usb

---

### Post by jacob01 on 2007-08-10
also the dell bios doesn't give many options, i dont think

---

### Post by sciurus on 2007-08-10
Kernels since 2.2.18 have USB. This isn't new technology.

---

### Post by jacob01 on 2007-08-11
well then i must be having other problems if the open suse live cd doesnt work with my key board

---

### Post by gl0wst1ckn1nja on 2007-08-12
sometimes it catches my keyboard sometimes not ... its not consistent at all

---

### Post by cacycleworks on 2007-08-12
> **gl0wst1ckn1nja said:**
> sometimes it catches my keyboard sometimes not ... its not consistent at all

Maybe try putting a cheap USB hub in between the kybd+mouse and the computer. That other OS for the lemmings reads serial so slowly that it covers up small glitches in motherboard manufacturers. Linux reads serial so efficiently that it will trip over the glitch... The hub helps to control the inputs from kybd+mouse to the motherboard.

Most "problems" I have seen with computers and linux can eventually be traced to a configuration or improper driver. Critique the logs, learn what hardware you have, investigate what software/modules are running on your computer to operate said hardware.

You can force the loading of modules upon boot to ensure compatability.

----------------------------------
As far as SUSE live CD, how come this is a posting here? Did you try the Kubuntu or Ubuntu live CDs? When we started testing on Dimensions, we found that knoppix and ubuntu were the easiest installs. 
-------------------------
When you get errors, use another computer and search google for the exact phrase, but prepend the OS and post-fix the computer. If the SUSE live CD halts with some gibberish (pretend it is: System Halted: No drives found) then you google for the string:
SuSe "System Halted: No drives found" Dell C521

And there normally is pages of answers to help you.
-------------------------
And about "what were they thinking"? That's a pretty open ended question. Probably they were thinking to minimize costs so as to continue to earn profits to stay in business while creating great value to ensure customers' continued loyalty.

It is the industry which drives change. When no motherboard package is offered with legacy ps2 or ancient huge connector, it does not make sense to pay for it to be added; which could add up to $100/board for a dedicated redesign.

Haha, besides, the industry needs to keep improving to handle all the bloat that MS pumps through. ;)

:)

---

### Post by gl0wst1ckn1nja on 2007-08-18
lol laptop = no usb mice or keyboard its the data ribbon that is direclty connected via motherboard.  good suggestions though

---

### Post by aldenhg on 2007-08-18
You realize that it's not the shape of the connector that matters but instead the bus it connects to, right? Laptops usually have their laptops and keyboards go in through a PS2 bus.

---

### Post by jb201116 on 2007-09-11
> **jacob01 said:**
> i bought a dell e520 n with ubuntu and when i found out it used a usb keyboard it kind of bothered me but then i thought "why would they sell a computer were you cant use it because the keyboard or mouse doest work" but any ways here i am typing to you and thinking wow they expect to sell this to a person who like to use linux who uses another distro. although other distros do have usb keyboard support to my knoledge, what if the one you use or want to try doesn't have usb support.

i ran into this problem when trying to boot from the open suse live cd which you'd think would have pretty good support being another pretty well known and well supported distro.

also dell did not include a ps/2 port like the older computers used

is there a fix or am i the only one

why did they not include an alternative port on a linux computer since usb keyboards are not that old

i tried the distro in a virtual machine and it worked great but a bit slow

you may want to take this into consideration when buying a dell

the only thing i could come up with for why they do that, is adding another port for just the linux computers would cost to much because they would have to use differant motherboads



It is a simple solution... upgrade the bios to the latest version on the dell site then make sure the network controller drivers are updated

Then run Ubuntu, no problems... 

cheers
jb201116

---

### Post by RedAFlame570 on 2007-09-12
If you are asking about new Dells, I think they phased out the PS2 port in favor of USB on all the new moels.  I have a dell Dimension C521 and it uses USB but there are no PS2 ports.  I am happy with what I have.

---

