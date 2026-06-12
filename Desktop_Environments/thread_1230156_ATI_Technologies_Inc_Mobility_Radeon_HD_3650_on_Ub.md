---
title: "ATI Technologies Inc Mobility Radeon HD 3650 on Ubuntu 9.04"
date: 2009-08-03
forum: Desktop Environments
---

### Post by randomlyrandom on 2009-08-03
Hi,

I have following video card:

ATI Technologies Inc Mobility Radeon HD 3650

On my Lenovo W500 laptop running Ubuntu 9.04 Jaunty. I have catalyst 9.5 installed to support for desktop effects.

After enabling desktop effects, the computer became damn slow and switching between windows using alt+tab, minimizing and maximizing windows take a lot of time.

Also, if I want to change the computer resolution, the screen size shrinks but no change in resolution. Let me know if you know how to fix this.

Also, which drivers I should install to get proper desktop effects? Please suggest.

My lspci output below

ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)


Regards,
-P

---

### Post by Mia1990 on 2009-08-03
I don't know if this will fix it or not but under system-administration-hardware drivers you should find your drivers there if not then you could check out [envyNG]("http://albertomilone.com/nvidia_scripts1.html") its is synaptic it can tell you what driver you need to install.

---

### Post by khelben1979 on 2009-08-03
I suggest you turn off desktop effects so you're able to use the system properly.

Do you have a working Catalyst Control Center? It can display what version of the driver you're currently using. Experimenting with different version of the ATi driver might solve your problem regarding graphics speed.

Is that laptop a 32 or 64 bit system?

---

### Post by randomlyrandom on 2009-08-03
Thanks. Its a 32-bit system.

---

### Post by khelben1979 on 2009-08-03
[Catalyst version 9.7]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English") is the latest one for your card right now.

[ATi Catalyst - Wikipedia]("http://en.wikipedia.org/wiki/Catalyst_Control_Center") if you need further information about it.

---

### Post by randomlyrandom on 2009-08-04
I have this already. But the problem here is, once I enable desktop effects, computer becomes very slow. Minimize, maximize takes long time ~2-3 seconds. And even when I try to switch between windows using Alt+Tab, it takes long time. Is there a fix for this?

---

### Post by khelben1979 on 2009-08-04
You should probably send a report directly to AMD and describe this problem since they support Linux nowadays.

The Radeon HD 3650 for laptops haven't been out for very long and hopefully they will solve this problem as time moves on.

---

### Post by krazyd on 2009-08-04
The Catalyst drivers have problems with KDE's compositor. Either don't use catalyst or don't use KDE's desktop effects. (generally fglrx (catalyst) is pretty ****).

The open source drivers work well for everything except 3D, and the 3D support is rapidly improving. See here:
[http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg](http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg)
[http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg](http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg)

---

### Post by HavocXphere on 2009-08-04
[https://bugs.launchpad.net/bugs/351186](https://bugs.launchpad.net/bugs/351186)

There is a patch which fixes that problem, but it seems to have stability issues for some and it reduces 3d performance.

---

### Post by trent1980 on 2009-08-07
I have a lenovo w500 also running Jaunty 9.04 ...

Video: VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650


I've installed the drivers straight from ATI, I've tried the radeonhd drivers (like the wiki page says), I've tried EnvyNG to install the 8.600-Outbuntu2 ... they ALL cause my screen to go haywire and total computer lockup (hard power cycle is the only way to get out). 

1920x1200 is my resolution.

pnagral -- have you been able to install any driver that doesn't cause a crash?

---

### Post by randomlyrandom on 2009-08-10
Hi trent1980,

Yes, I am good now. I have installed this driver

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

And 3D effects works excellent. However, I am unable to use suspend, hibernate functionalities after installing this. Hope this helps you. Let me know if you are able to use suspend, hibernate after installing these drivers.

---

### Post by trent1980 on 2009-08-10
> **pnagral said:**
> Hi trent1980,

Yes, I am good now. I have installed this driver

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

And 3D effects works excellent. However, I am unable to use suspend, hibernate functionalities after installing this. Hope this helps you. Let me know if you are able to use suspend, hibernate after installing these drivers.


In the bios, there is a setting to change your video (if you have the w500) to "discrete" instead of "integrated" or "switchable" (also turn off auto sensing). With it set on "discrete" I can use the ati driver that comes with ubuntu but I downloaded the installer from ati and it also works good.

[http://www.linuxquestions.org/questions/slackware-14/unable-to-start-x-after-installing-fglrx-669163/](http://www.linuxquestions.org/questions/slackware-14/unable-to-start-x-after-installing-fglrx-669163/)

my suspend is working with the fix above but I didn't try yours

---

### Post by randomlyrandom on 2009-08-14
Ok. Let me try this and get back to you.

---

### Post by Bashar &quot; on 2009-08-30
> **pnagral said:**
> Ok. Let me try this and get back to you.

any good news for W500 owners?

---

### Post by trent1980 on 2009-08-31
> **Bashar " said:**
> any good news for W500 owners?

Well ... i've done so many things but i finally have my w500 working pretty smoothly.

I went back and started over with 8.04 but I could never get the wireless to work good (the video worked great though). Then I upgraded to intrepid and things worked better but the wireless still was giving me issues. I then went to jaunty and the wireless worked fine ... the video is a tad slower but nowhere near as bad as when I had first installed jaunty out of the box.

I'm not a big linux person so i can't explain why an upgrade works better ... but it did for me with my w500.

---

