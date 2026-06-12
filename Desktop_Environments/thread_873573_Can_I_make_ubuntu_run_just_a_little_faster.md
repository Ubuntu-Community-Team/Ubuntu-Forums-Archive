---
title: "Can I make ubuntu run just a little faster?"
date: 2008-07-29
forum: Desktop Environments
---

### Post by Fzang on 2008-07-29
I'm running ubuntu virtually with windows XP as host OS (linux can't run on my computer because of a BIOS bug :()

... But it's sorta slow sometimes

How can I speed up ubuntu, but still keep the ubuntu'ish look? I don't wanna rip it appart to something ugly, yet fast...

Most of all, I don't wanna let go of the top panel... it gives me a warm feeling >_>

So, any way I can speed it up for virtualization but still keep the look?

---

### Post by forger on 2008-07-29
What is your specification?
Computer brand / model? RAM size? Processor? Hard disk size?

Post back with the output of this command (in terminal):
```
sudo fdisk -l
```

You might be looking for ubuntu jeos:
[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)
or xubuntu:
[http://www.ubuntu.com/products/whatisubuntu/xubuntu](http://www.ubuntu.com/products/whatisubuntu/xubuntu)

---

### Post by Fzang on 2008-07-29
My virtual ubuntu doesn't really have any specs...? It has 1024 mb ram and 10 GB disk space... that's all

My host computer is a laptop with these specs:

Acer Aspire 5050

2,2 GHz AMD Turion Mobile Technology processor
Radeon Xpress 1100, 256 mb shared graphics card
Wireless Atheros AR5006EG chipset
2 GB RAM

Things I know: Ubuntu doesn't support any of my hardware, Mandriva supports all hardware (woop de doo!)

.... But because of this dam messed up BIOS bug thing of the ACPI, all versions of linux hangs on boot unless I turn wireless completely off at all times (but then the computer is useless...)

So.... yea..

---

### Post by TenPlus1 on 2008-07-29
Pop into Services and Sessions and turn OFF those that you dont need/use...  I turn Tracker off because it slows down disk access and also remove anything from the gnome-bar that I dont need either...

Pop in here for some more tweaks: [http://www.ubuntu-unleashed.com/2008/04/tweak-and-optimize-ubuntu-linux-boot.html](http://www.ubuntu-unleashed.com/2008/04/tweak-and-optimize-ubuntu-linux-boot.html)

---

