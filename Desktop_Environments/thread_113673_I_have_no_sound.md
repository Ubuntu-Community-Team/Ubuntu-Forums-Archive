---
title: "I have no sound"
date: 2006-01-06
forum: Desktop Environments
---

### Post by ch13f121 on 2006-01-06
Ok, I have no sound on my pc in ubuntu, and I'm using an SB Live! 24-bit sound card, the onboard's disabled.  Do I go thru Xorg to config my sound card?  I dunno waht to do here, I'm still the ubuntu noob.  I put it on my primary machine, as a secondary OS.  anyway  I have another question as well, I have an ati 9600se, where would I find the drivers for this card?

---

### Post by zappa86 on 2006-01-06
You should open up a terminal and do a dmesg and see if you can find any information relating to sound. (if it just provides too much infomation you can use grep to narrow it down [dmesg | grep pci] or something to get the info you want) Also, you could try to open alsamixer and see if it can find your sound device. I know creative makes a live 24 bit external usb thing? is that the one you are using or the internal PCI one. Also I just found this link:
[http://www.ubuntuforums.org/showthread.php?t=19307&page=1]("http://www.ubuntuforums.org/showthread.php?t=19307&page=1")
I'm wondering if that helps at all

---

### Post by ch13f121 on 2006-01-06
I'm using a PCI internal sb live! 24-bit sound card.  alright, if it finds it in dmesg or anything, what do I do from there?

---

### Post by zappa86 on 2006-01-06
when you open alsamixer up at top it will say your card and chip, is it listed or does it give you some error?

---

### Post by ch13f121 on 2006-01-06
hehe I should asked this earlier, how do I get into alsamixer?

---

### Post by ch13f121 on 2006-01-06
I know this is a double post, but I feel retarded now lmao I unmuted the Analog Front thing...and turned it up...and it worked, but I dunno how or why the thing was muted, on a fresh install.

---

### Post by FloSynergy on 2006-03-23
hey there,

i'm dealing with similar issues....

audigy 2 zs pcmcia sound card running on kubuntu in asus a2 notebook.
onboard card is fried, so i needed a new one.

managed to install drivers ok, kmixer now recognises the existence of the card,
but i can't get it to play sound, and the system seems to consider the onboard card to be primary.

how do i disable the onboard sound?

thanks, flo

---

