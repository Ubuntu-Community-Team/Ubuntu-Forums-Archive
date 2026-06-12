---
title: "Ubuntu install freezes at hardware detection!"
date: 2005-10-16
forum: Desktop Environments
---

### Post by henrypootel on 2005-10-16
I was very excited to get 5.10 onto my PC at home, so i threw the cd in, and  started up.
I entered 'expert' at the prompt, and watched all the pretty messages go past, and then...... that was it.
The scrolling text stuff stopped just after saying something abour using a PS2 mouse, and some stuff about USB hubs etc...
And it just sits there. I tried unplugging some devices, and it displays everything that is happening(ie. USB hub has disconnected etc...).

I have tried the install using the 'noapic' 'nolapic' and 'acpi=off' arguments, as well as just a standard install, but none of them work.

It's running on a MSI Mega 865(Intel 865 chipset), with a p42.6GhzHT CPU, 1536 megs of RAM, Geforce4MX graphics card, and a Seagate Barracuda 200Gb SATA HDD.

Can anyone help me?
I know that i can just install hoary(which installed without a hitch, and worked fine for me for several months), and then upgrade using the cd, but i would much rather do a 'clean' install.

---

### Post by sedi on 2005-10-16
I'd say the problem is your hard disk. I have an S-ATA hard disk as well and I can't install 5.10 either but 5.04 worked fine. Do you get any error message concerning libata?

---

### Post by henrypootel on 2005-10-16
No, i didn't notice any error messages go by(may have been to fast).
I will check that out when i get home.
In the meantime, if i install to an PATA drive, image it and then restore it to the partition on my SATA, will that break it, or should that work?

Otherwise, is there any way to get my SATA driver in there(or whatever it needs)?

---

### Post by sedi on 2005-10-17
I'm pretty sure that you can install 5.10 to your PATA drive. But I don't know if it works when you image it and restore it to your SATA drive. I have a 5.10 install on my computer that I can't access but it's on my hard disk. I'd just try it if I had the time.

---

### Post by henrypootel on 2005-10-17
I didn't have time to try that out last night, but i checked the install again, and at the top of the screen it seems to be showing that the HDD was detected properly. It says something about Sareial ATA devices, and i saw a mention of the drive's model number, so that seems to be fine.
Also, the Live CD fails at the same point, which i would have thought would not access the HDD.
This is all made more annoying by the fact that Hoary and Warty all installed fine!
Can i grab components from the hoary install cd and load them, or add some drivers or something to my breezy cd to make it load properly?

please help me!

---

