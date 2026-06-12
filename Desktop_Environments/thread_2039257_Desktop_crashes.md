---
title: "Desktop crashes"
date: 2012-08-08
forum: Desktop Environments
---

### Post by yadayada2 on 2012-08-08
Hi

For a weeks now I have experienced problems with my desktop. I run Ubuntu 12.04 with Unity on a ThinkPad T420. Sometimes I just get a message "System crash detected. And sometimes my entire desktop environment crashes and then I find myself confronted with the greeter again.

What should I do? Where should I look for help/fixes?

Best regards

---

### Post by lukeiamyourfather on 2012-08-08
I have a ThinkPad T420 as well but have not experienced this. What graphics driver are you using, does it have the Intel only graphics or the Nvidia hybrid graphics? Have you run the hardware diagnostics that come with the laptop?

---

### Post by yadayada2 on 2012-08-09
First, this is the output of lspci:

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 08)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 04)

```

Where should I look to see, which graphics driver I use?

---

### Post by yadayada2 on 2012-08-10
bump :(

---

### Post by asipper on 2012-08-10
Have you tried reinstalling?   Sometimes that helps if the installer had any problems.

---

### Post by yadayada2 on 2012-08-11
No, I had no problems with the installation. And at first, the operating system and desktop environment worked fine. Therefore I think it may have to with some update in the meantime.

---

### Post by yadayada2 on 2012-08-21
Does no one have a clue how to solve this? :(

---

### Post by 5l4y3r on 2012-08-23
Have you tried to use Ubuntu 2D?

---

### Post by yadayada2 on 2012-08-24
No, because that was a suggested solution in another thread, but many people reported that it does not help at all.

---

