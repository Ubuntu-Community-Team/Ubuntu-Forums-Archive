---
title: "Hard drive wear and Dell 1420"
date: 2008-01-15
forum: Dell  Ubuntu Support
---

### Post by Speidereyes on 2008-01-15
I have come across a few posts regarding aggressive power management  in Ubuntu and how it can contribute to premature hard drive wear. Is this an issue with the Dell 1420 (Vista preload)? I have just installed Gutsy (regular 32 bit edition, not the Dell remaster) on a 1420 and wanted to make sure I was OK. If this is an issue, would it be solved by installing the Dell remaster even though my laptop was not preloaded with Ubuntu?

Thanks for any help.

---

### Post by b4d on 2008-01-16
I have similar problem, only I am concerned because my disk makes strange clicky noise every few seconds in idle mode... 1520 inspiron is the laptop...

---

### Post by natehall on 2008-01-16
If you'd like to check on the status of your hard drive do this:

sudo apt-get install smartmontools
sudo smartctl -a /dev/sda

There is a [sticky post]("http://ubuntuforums.org/showthread.php?t=591503&highlight=ubuntudemon") on this by ubuntu_demon. That's where I got this bit of code.

---

### Post by Speidereyes on 2008-01-17
Thanks for the replies. This seems to be a pretty complicated issue. I was hoping that this would not be a problem for an officially supported laptop (even  if mine came with Vista rather than Ubuntu) but I guess that is not so simple. The reading gives me a 28000 load cycle count after a little over 3 months of use (I cannot even guess how many hours I have used this laptop). This seems to be an OK figure if the average HD is supposed to last at least 600,000.

---

### Post by ikkepjo on 2008-01-17
Even if it may seem complicated, just go for it. I have an 1150, and my hard disk got killed by this (I suspect, I became only aware of the issue after it was killed). 28000 is A LOT, my new HD is in the 2000 range after 3 months, but then I set it to the absolute minimum.

Regards,

Peter


> **Speidereyes said:**
> Thanks for the replies. This seems to be a pretty complicated issue. I was hoping that this would not be a problem for an officially supported laptop (even  if mine came with Vista rather than Ubuntu) but I guess that is not so simple. The reading gives me a 28000 load cycle count after a little over 3 months of use (I cannot even guess how many hours I have used this laptop). This seems to be an OK figure if the average HD is supposed to last at least 600,000.

---

### Post by Speidereyes on 2008-01-17
Thank you for the advice.

---

### Post by Speidereyes on 2008-01-17
I applied the fix by ubuntu_demon as it clearly appeared that my load cycle count was increasing every few minutes even with AC plugged in. I went from 28800 to 28950 cycles in about an hour or so. Does anyone know if this an issue for Dell notebooks that came with Ubuntu preinstalled?

---

