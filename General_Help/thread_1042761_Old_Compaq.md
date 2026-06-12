---
title: "Old Compaq"
date: 2009-01-17
forum: General Help
---

### Post by theozzlives on 2009-01-17
How does one find out the settings of a motherboard that the manufacturer doesn't even recognise any more. I have a Compaq that's overclocked and I want to set the clock right.

---

### Post by cariboo on 2009-01-17
HP/Compaq have really good documentation, I've found manuals for my Comapq desktop, I'm not sure what the model is anymore, but it runs a 350Mhz PII and I can still get a manual for my ancient HP 5P laser printer. If you can post the model number, I can probably provide you with a link.

Jim

---

### Post by Cap'n Skyler on 2009-01-17
> **theozzlives said:**
> How does one find out the settings of a motherboard that the manufacturer doesn't even recognise any more. I have a Compaq that's overclocked and I want to set the clock right.
the bios doent have a reset or default setting option?
most of my comps do i think.i saw it when i was changing the boot sequence 
to instal linux.

---

### Post by linux_tech on 2009-01-17
Power on your computer and press the key on your keyboard to enter the BIOS. This is typically the Delete key, F1, F2, or F10.
Go to the last tab or page of your BIOS,
Select option similar to "restore factory settings"
Save your changes (F10)key

---

### Post by theozzlives on 2009-01-18
That's how old it is, the frequency is not in the CMOS Setup (jumpers)

---

### Post by linux_tech on 2009-01-18
Maybe you can reset either via jumpers
[http://www.wikihow.com/Reset-Your-BIOS](http://www.wikihow.com/Reset-Your-BIOS)

or unplug cmos battery

---

### Post by TVTrukChik on 2009-01-18
This site has a lot of info on older hardware, jumper settings, etc: [http://hardwarehell.com/index.shtml]("http://hardwarehell.com/index.shtml")

---

### Post by theozzlives on 2009-01-18
> **cariboo907 said:**
> HP/Compaq have really good documentation, I've found manuals for my Comapq desktop, I'm not sure what the model is anymore, but it runs a 350Mhz PII and I can still get a manual for my ancient HP 5P laser printer. If you can post the model number, I can probably provide you with a link.

Jim

The only number I have is C-132104, it's a Compaq Deskpro. Ubuntu's cpuinfo says it's a 400 MHz, but Windows says it's 384 or some odd number like that. That's what makes me think a previous owner overclocked it.

---

### Post by abn91c on 2009-01-18
try removing the CMOS battery to clear the bios.

---

### Post by DeMus on 2009-01-18
> **theozzlives said:**
> The only number I have is C-132104, it's a Compaq Deskpro. Ubuntu's cpuinfo says it's a 400 MHz, but Windows says it's 384 or some odd number like that. That's what makes me think a previous owner overclocked it.

The difference between 384 and 400MHz can be caused by the system throttling down the processor since it has nothing to do. You probably have a 400Mhz processor which used to be a normal type of processor in the old days. I'm pretty sure it is NOT overclocked.
Don't worry about it. Just install the software you want to install and have fun with it.

---

