---
title: "WiFi don't work"
date: 2011-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CCapslocKK on 2011-05-12
Hi,
My Dell Inspiron 510m with Ubuntu 10.04 don't detect any WiFi network :(.
I like my Ubuntu but this problem anyone knows how to fix it :confused:
Thanks if you can help me

---

### Post by mikewhatever on 2011-05-14
Hi there, and welcome to the forums. You'll need to post a moderate amount of technical info. From a Terminal window, post the outputs of the following:
```
ifconfig

lspci

lsmod
```

---

### Post by CCapslocKK on 2011-05-14
> **mikewhatever said:**
> Hi there, and welcome to the forums. You'll need to post a moderate amount of technical info. From a Terminal window, post the outputs of the following:
```
ifconfig
 
lspci
 
lsmod
```
 
 
inspiron@Inspiron:~$ ifconfig 
eth0 Link encap:Ethernet Endereço de HW 00:11:43:41:d8:b8 
inet end.: 192.168.0.2 Bcast:192.168.0.255 Masc:255.255.255.0 
UP BROADCAST MULTICAST MTU:1500 Métrica:1 
pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0 
Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0 
colisões:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 


lo Link encap:Loopback Local 
inet end.: 127.0.0.1 Masc:255.0.0.0 
endereço inet6: ::1/128 Escopo:Máquina 
UP LOOPBACK RUNNING MTU:16436 Métrica:1 
pacotes RX:628 erros:0 descartados:0 excesso:0 quadro:0 
Pacotes TX:628 erros:0 descartados:0 excesso:0 portadora:0 
colisões:0 txqueuelen:0 
RX bytes:50104 (50.1 KB) TX bytes:50104 (50.1 KB) 


inspiron@Inspiron:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) 
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02) 
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller 
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04) 
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81) 
inspiron@Inspiron:~$ lsmod 
Module Size Used by 
usbserial 33694 0 
binfmt_misc 6587 1 
fbcon 35102 71 
tileblit 2031 1 fbcon 
font 7557 1 fbcon 
bitblit 4707 1 fbcon 
softcursor 1189 1 bitblit 
vga16fb 11385 0 
vgastate 8961 1 vga16fb 
snd_intel8x0 25652 2 
snd_ac97_codec 100646 1 snd_intel8x0 
ac97_bus 1002 1 snd_ac97_codec 
pcmcia 30784 0 
snd_pcm_oss 35308 0 
snd_mixer_oss 13746 1 snd_pcm_oss 
snd_pcm 70694 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
snd_seq_dummy 1338 0 
snd_seq_oss 26722 0 
snd_seq_midi 4557 0 
joydev 8740 0 
snd_rawmidi 19056 1 snd_seq_midi 
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi 
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer 19098 2 snd_pcm,snd_seq 
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
ipw2100 66395 0 
yenta_socket 20408 1 
rsrc_nonstatic 10015 1 yenta_socket 
libipw 39896 1 ipw2100 
snd 54180 14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
i915 287810 3 
lib80211 5046 1 libipw 
ppdev 5259 0 
pcmcia_core 32964 3 pcmcia,yenta_socket,rsrc_nonstatic 
dell_wmi 1793 0 
drm_kms_helper 29329 1 i915 
lp 7028 0 
psmouse 63245 0 
intel_agp 24375 2 i915 
soundcore 6620 1 snd 
dcdbas 5422 0 
parport_pc 25962 1 
drm 162345 4 i915,drm_kms_helper 
i2c_algo_bit 5028 1 i915 
serio_raw 3978 0 
parport 32635 3 ppdev,lp,parport_pc 
shpchp 28835 0 
snd_page_alloc 7076 2 snd_intel8x0,snd_pcm 
agpgart 31724 2 intel_agp,drm 
video 17375 1 i915 
output 1871 1 video 
usbhid 36110 0 
ohci1394 26950 0 
hid 67096 1 usbhid 
e100 28211 0 
ieee1394 81181 1 ohci1394 
mii 4381 1 e100 
inspiron@Inspiron:~$

---

### Post by holiday on 2011-05-14
Is your wireless enabled on your laptop? I've done this so many times so even though you may think me silly I have to ask. I've often inadvertently switched off my wireless while moving my laptop.

There's a switch on your laptop somewhere to enable/disable wireless. Make sure that's enabled. On my laptop, Ubuntu doesn't warn me.

---

### Post by CCapslocKK on 2011-05-14
I don't know if its enabled or not. The only way to enable wireless on my laptop that i know is by the keys Fn-F2, but they don't response nothing. There is not other way that i know.

---

### Post by TravisNRG on 2011-05-14
> **CCapslocKK said:**
> I don't know if its enabled or not. The only way to enable wireless on my laptop that i know is by the keys Fn-F2, but they don't response nothing. There is not other way that i know.

i have the same problem... with my dell inpiron 1525

its the hardware, my ethernet works but wifi does not...

i dont yet know how to fix this problem.. i wish i could.

not quite sure how to get a driver for it...

---

### Post by mikewhatever on 2011-05-14
Thanks a bunch for the outputs. I am not quite sure what's wrong there. The module, ipw2100, seems to be loaded, but the wireless interface is not present. Can you also post the output of the following:
```
dmesg | grep ipw
```

---

### Post by ngronewold on 2011-05-14
> **CCapslocKK said:**
> I don't know if its enabled or not. The only way to enable wireless on my laptop that i know is by the keys Fn-F2, but they don't response nothing. There is not other way that i know.

This issue with Dell Inspiron laptops was solved on the sticky thread at the top of the wireless advice section. There you will find directions on downloading packages via synaptic, but I think you'll need to be connected to the Internet via a land line.

---

### Post by CCapslocKK on 2011-05-15
> **mikewhatever said:**
> Thanks a bunch for the outputs. I am not quite sure what's wrong there. The module, ipw2100, seems to be loaded, but the wireless interface is not present. Can you also post the output of the following:
```
dmesg | grep ipw
```
 
Hi,
Here is the output of "dmesg" only. The ohter one, "grep ipw" does not response anything.
 
 
inspiron@Inspiron:~$ dmesg


[ 0.185022] pnp 00:0d: io resource (0xebc0-0xebdf) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xefff), disabling 
[ 0.185028] pnp 00:0d: io resource (0xefb0-0xefbb) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xefff), disabling 
[ 0.185033] pnp 00:0d: io resource (0xefc0-0xefdf) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xefff), disabling 
[ 0.186171] pnp: PnP ACPI: found 14 devices 
[ 0.186174] ACPI: ACPI bus type pnp unregistered 
[ 0.186179] PnPBIOS: Disabled by ACPI PNP 
[ 0.186194] system 00:00: iomem range 0x0-0x9fbff could not be reserved 
[ 0.186199] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved 
[ 0.186203] system 00:00: iomem range 0xc0000-0xcffff could not be reserved 
[ 0.186208] system 00:00: iomem range 0xe0000-0xfffff could not be reserved 
[ 0.186213] system 00:00: iomem range 0x100000-0x4feeffff could not be reserved 
[ 0.186217] system 00:00: iomem range 0x4fef0000-0x4fefffff has been reserved 
[ 0.186222] system 00:00: iomem range 0xfec10000-0xfec1ffff has been reserved 
[ 0.186226] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved 
[ 0.186231] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved 
[ 0.186240] system 00:02: ioport range 0x4d0-0x4d1 has been reserved 
[ 0.186249] system 00:03: ioport range 0xf400-0xf4fe has been reserved 
[ 0.186254] system 00:03: ioport range 0x880-0x8bf has been reserved 
[ 0.186258] system 00:03: ioport range 0x8c0-0x8df has been reserved 
[ 0.186262] system 00:03: ioport range 0x8e0-0x8ff has been reserved 
[ 0.186272] system 00:08: ioport range 0x900-0x97f has been reserved 
[ 0.186281] system 00:0d: ioport range 0x7b0-0x7bb has been reserved 
[ 0.186286] system 00:0d: ioport range 0x7c0-0x7df has been reserved 
[ 0.186290] system 00:0d: ioport range 0xbb0-0xbbb has been reserved 
[ 0.186294] system 00:0d: ioport range 0xbc0-0xbdf has been reserved 
[ 0.186298] system 00:0d: ioport range 0xfb0-0xfbb has been reserved 
[ 0.186303] system 00:0d: ioport range 0xfc0-0xfdf has been reserved 
[ 0.186307] system 00:0d: ioport range 0x13b0-0x13bb has been reserved 
[ 0.186312] system 00:0d: ioport range 0x13c0-0x13df has been reserved 
[ 0.186316] system 00:0d: ioport range 0x17b0-0x17bb has been reserved 
[ 0.186320] system 00:0d: ioport range 0x17c0-0x17df has been reserved 
[ 0.186325] system 00:0d: ioport range 0x1bb0-0x1bbb has been reserved 
[ 0.186329] system 00:0d: ioport range 0x1bc0-0x1bdf has been reserved 
[ 0.186334] system 00:0d: ioport range 0x1fb0-0x1fbb has been reserved 
[ 0.186338] system 00:0d: ioport range 0x1fc0-0x1fdf has been reserved 
[ 0.186342] system 00:0d: ioport range 0x23b0-0x23bb has been reserved 
[ 0.186347] system 00:0d: ioport range 0x23c0-0x23df has been reserved 
[ 0.186351] system 00:0d: ioport range 0x27b0-0x27bb has been reserved 
[ 0.186356] system 00:0d: ioport range 0x27c0-0x27df has been reserved 
[ 0.186360] system 00:0d: ioport range 0x2bb0-0x2bbb has been reserved 
[ 0.186365] system 00:0d: ioport range 0x2bc0-0x2bdf has been reserved 
[ 0.186369] system 00:0d: ioport range 0x2fb0-0x2fbb has been reserved 
[ 0.186374] system 00:0d: ioport range 0x2fc0-0x2fdf has been reserved 
[ 0.186378] system 00:0d: ioport range 0x33b0-0x33bb has been reserved 
[ 0.186383] system 00:0d: ioport range 0x33c0-0x33df has been reserved 
[ 0.186387] system 00:0d: ioport range 0x37b0-0x37bb has been reserved 
[ 0.186392] system 00:0d: ioport range 0x37c0-0x37df has been reserved 
[ 0.186396] system 00:0d: ioport range 0x3bb0-0x3bbb has been reserved 
[ 0.186401] system 00:0d: ioport range 0x3bc0-0x3bdf has been reserved 
[ 0.186405] system 00:0d: ioport range 0x3fb0-0x3fbb has been reserved 
[ 0.186410] system 00:0d: ioport range 0x3fc0-0x3fdf has been reserved 
[ 0.186414] system 00:0d: ioport range 0x43b0-0x43bb has been reserved 
[ 0.186419] system 00:0d: ioport range 0x43c0-0x43df has been reserved 
[ 0.186423] system 00:0d: ioport range 0x47b0-0x47bb has been reserved 
[ 0.186428] system 00:0d: ioport range 0x47c0-0x47df has been reserved 
[ 0.186433] system 00:0d: ioport range 0x4bb0-0x4bbb has been reserved 
[ 0.186437] system 00:0d: ioport range 0x4bc0-0x4bdf has been reserved 
[ 0.186442] system 00:0d: ioport range 0x4fb0-0x4fbb has been reserved 
[ 0.186446] system 00:0d: ioport range 0x4fc0-0x4fdf has been reserved 
[ 0.186451] system 00:0d: ioport range 0x53b0-0x53bb has been reserved 
[ 0.186456] system 00:0d: ioport range 0x53c0-0x53df has been reserved 
[ 0.186460] system 00:0d: ioport range 0x57b0-0x57bb has been reserved 
[ 0.186465] system 00:0d: ioport range 0x57c0-0x57df has been reserved 
[ 0.186469] system 00:0d: ioport range 0x5bb0-0x5bbb has been reserved 
[ 0.186474] system 00:0d: ioport range 0x5bc0-0x5bdf has been reserved 
[ 0.186479] system 00:0d: ioport range 0x5fb0-0x5fbb has been reserved 
[ 0.186483] system 00:0d: ioport range 0x5fc0-0x5fdf has been reserved 
[ 0.186488] system 00:0d: ioport range 0x63b0-0x63bb has been reserved 
[ 0.186493] system 00:0d: ioport range 0x63c0-0x63df has been reserved 
[ 0.186497] system 00:0d: ioport range 0x67b0-0x67bb has been reserved 
[ 0.186502] system 00:0d: ioport range 0x67c0-0x67df has been reserved 
[ 0.186507] system 00:0d: ioport range 0x6bb0-0x6bbb has been reserved 
[ 0.186512] system 00:0d: ioport range 0x6bc0-0x6bdf has been reserved 
[ 0.186516] system 00:0d: ioport range 0x6fb0-0x6fbb has been reserved 
[ 0.186521] system 00:0d: ioport range 0x6fc0-0x6fdf has been reserved 
[ 0.186526] system 00:0d: ioport range 0x73b0-0x73bb has been reserved 
[ 0.186530] system 00:0d: ioport range 0x73c0-0x73df has been reserved 
[ 0.186535] system 00:0d: ioport range 0x77b0-0x77bb has been reserved 
[ 0.186540] system 00:0d: ioport range 0x77c0-0x77df has been reserved 
[ 0.186545] system 00:0d: ioport range 0x7bb0-0x7bbb has been reserved 
[ 0.186549] system 00:0d: ioport range 0x7bc0-0x7bdf has been reserved 
[ 0.186554] system 00:0d: ioport range 0x7fb0-0x7fbb has been reserved 
[ 0.186559] system 00:0d: ioport range 0x7fc0-0x7fdf has been reserved 
[ 0.186564] system 00:0d: ioport range 0x83b0-0x83bb has been reserved 
[ 0.186569] system 00:0d: ioport range 0x83c0-0x83df has been reserved 
[ 0.186574] system 00:0d: ioport range 0x87b0-0x87bb has been reserved 
[ 0.186578] system 00:0d: ioport range 0x87c0-0x87df has been reserved 
[ 0.186583] system 00:0d: ioport range 0x8bb0-0x8bbb has been reserved 
[ 0.186588] system 00:0d: ioport range 0x8bc0-0x8bdf has been reserved 
[ 0.186593] system 00:0d: ioport range 0x8fb0-0x8fbb has been reserved 
[ 0.186598] system 00:0d: ioport range 0x8fc0-0x8fdf has been reserved 
[ 0.186602] system 00:0d: ioport range 0x93b0-0x93bb has been reserved 
[ 0.186607] system 00:0d: ioport range 0x93c0-0x93df has been reserved 
[ 0.186612] system 00:0d: ioport range 0x97b0-0x97bb has been reserved 
[ 0.186617] system 00:0d: ioport range 0x97c0-0x97df has been reserved 
[ 0.186622] system 00:0d: ioport range 0x9bb0-0x9bbb has been reserved 
[ 0.186627] system 00:0d: ioport range 0x9bc0-0x9bdf has been reserved 
[ 0.186632] system 00:0d: ioport range 0x9fb0-0x9fbb has been reserved 
[ 0.186637] system 00:0d: ioport range 0x9fc0-0x9fdf has been reserved 
[ 0.186642] system 00:0d: ioport range 0xa3b0-0xa3bb has been reserved 
[ 0.186646] system 00:0d: ioport range 0xa3c0-0xa3df has been reserved 
[ 0.186651] system 00:0d: ioport range 0xa7b0-0xa7bb has been reserved 
[ 0.186656] system 00:0d: ioport range 0xa7c0-0xa7df has been reserved 
[ 0.186661] system 00:0d: ioport range 0xabb0-0xabbb has been reserved 
[ 0.186666] system 00:0d: ioport range 0xabc0-0xabdf has been reserved 
[ 0.186671] system 00:0d: ioport range 0xafb0-0xafbb has been reserved 
[ 0.186676] system 00:0d: ioport range 0xafc0-0xafdf has been reserved 
[ 0.186681] system 00:0d: ioport range 0xb3b0-0xb3bb has been reserved 
[ 0.186686] system 00:0d: ioport range 0xb3c0-0xb3df has been reserved 
[ 0.186691] system 00:0d: ioport range 0xb7b0-0xb7bb has been reserved 
[ 0.186696] system 00:0d: ioport range 0xb7c0-0xb7df has been reserved 
[ 0.186701] system 00:0d: ioport range 0xbbb0-0xbbbb has been reserved 
[ 0.186706] system 00:0d: ioport range 0xbbc0-0xbbdf has been reserved 
[ 0.186711] system 00:0d: ioport range 0xbfb0-0xbfbb has been reserved 
[ 0.186716] system 00:0d: ioport range 0xbfc0-0xbfdf has been reserved 
[ 0.186721] system 00:0d: ioport range 0xc3b0-0xc3bb has been reserved 
[ 0.186726] system 00:0d: ioport range 0xc3c0-0xc3df has been reserved 
[ 0.186731] system 00:0d: ioport range 0xc7b0-0xc7bb has been reserved 
[ 0.186736] system 00:0d: ioport range 0xc7c0-0xc7df has been reserved 
[ 0.186742] system 00:0d: ioport range 0xcbb0-0xcbbb has been reserved 
[ 0.186751] system 00:0d: ioport range 0xcbc0-0xcbdf has been reserved 
[ 0.186757] system 00:0d: ioport range 0xcfb0-0xcfbb has been reserved 
[ 0.186762] system 00:0d: ioport range 0xcfc0-0xcfdf has been reserved 
[ 0.186767] system 00:0d: ioport range 0xd3b0-0xd3bb has been reserved 
[ 0.186772] system 00:0d: ioport range 0xd3c0-0xd3df has been reserved 
[ 0.186777] system 00:0d: ioport range 0xd7b0-0xd7bb has been reserved 
[ 0.186782] system 00:0d: ioport range 0xd7c0-0xd7df has been reserved 
[ 0.186787] system 00:0d: ioport range 0xdbb0-0xdbbb has been reserved 
[ 0.186793] system 00:0d: ioport range 0xdbc0-0xdbdf has been reserved 
[ 0.186798] system 00:0d: ioport range 0xdfb0-0xdfbb has been reserved 
[ 0.186803] system 00:0d: ioport range 0xdfc0-0xdfdf has been reserved 
[ 0.186812] system 00:0d: ioport range 0xf3b0-0xf3bb has been reserved 
[ 0.186818] system 00:0d: ioport range 0xf3c0-0xf3df has been reserved 
[ 0.186823] system 00:0d: ioport range 0xf7b0-0xf7bb has been reserved 
[ 0.186828] system 00:0d: ioport range 0xf7c0-0xf7df has been reserved 
[ 0.186833] system 00:0d: ioport range 0xfbb0-0xfbbb has been reserved 
[ 0.186839] system 00:0d: ioport range 0xfbc0-0xfbdf has been reserved 
[ 0.186844] system 00:0d: ioport range 0xffb0-0xffbb has been reserved 
[ 0.186853] system 00:0d: ioport range 0xffc0-0xffdf has been reserved 
[ 0.221602] pci 0000:01:01.0: CardBus bridge, secondary bus 0000:02 
[ 0.221606] pci 0000:01:01.0: IO window: 0x00e000-0x00e0ff 
[ 0.221612] pci 0000:01:01.0: IO window: 0x00e400-0x00e4ff 
[ 0.221618] pci 0000:01:01.0: PREFETCH window: 0x50000000-0x53ffffff 
[ 0.221624] pci 0000:01:01.0: MEM window: 0x58000000-0x5bffffff 
[ 0.221629] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01 
[ 0.221634] pci 0000:00:1e.0: IO window: 0xe000-0xefff 
[ 0.221641] pci 0000:00:1e.0: MEM window: 0xfc000000-0xfdffffff 
[ 0.221647] pci 0000:00:1e.0: PREFETCH window: 0x50000000-0x53ffffff 
[ 0.221664] pci 0000:00:1e.0: setting latency timer to 64 
[ 0.221674] pci 0000:01:01.0: enabling device (0000 -> 0003) 
[ 0.221889] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11 
[ 0.221892] PCI: setting IRQ 11 as level-triggered 
[ 0.221899] pci 0000:01:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11 
[ 0.221909] pci_bus 0000:00: resource 0 io: [0x00-0xffff] 
[ 0.221913] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff] 
[ 0.221917] pci_bus 0000:01: resource 0 io: [0xe000-0xefff] 
[ 0.221921] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff] 
[ 0.221925] pci_bus 0000:01: resource 2 pref mem [0x50000000-0x53ffffff] 
[ 0.221929] pci_bus 0000:01: resource 3 io: [0x00-0xffff] 
[ 0.221933] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff] 
[ 0.221937] pci_bus 0000:02: resource 0 io: [0xe000-0xe0ff] 
[ 0.221941] pci_bus 0000:02: resource 1 io: [0xe400-0xe4ff] 
[ 0.221945] pci_bus 0000:02: resource 2 pref mem [0x50000000-0x53ffffff] 
[ 0.221949] pci_bus 0000:02: resource 3 mem: [0x58000000-0x5bffffff] 
[ 0.221991] NET: Registered protocol family 2 
[ 0.222113] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[ 0.222543] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[ 0.223793] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[ 0.224627] TCP: Hash tables configured (established 131072 bind 65536) 
[ 0.224632] TCP reno registered 
[ 0.224788] NET: Registered protocol family 1 
[ 0.224824] pci 0000:00:02.0: Boot video device 
[ 0.224915] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling 
[ 0.225171] cpufreq-nforce2: No nForce2 chipset. 
[ 0.225241] Scanning for low memory corruption every 60 seconds 
[ 0.225422] audit: initializing netlink socket (disabled) 
[ 0.225446] type=2000 audit(1305469554.225:1): initialized 
[ 0.240350] Trying to unpack rootfs image as initramfs... 
[ 0.257558] highmem bounce pool size: 64 pages 
[ 0.257566] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[ 0.259792] VFS: Disk quotas dquot_6.5.2 
[ 0.259874] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[ 0.265739] fuse init (API version 7.13) 
[ 0.265873] msgmni has been set to 1709 
[ 0.266169] alg: No test for stdrng (krng) 
[ 0.266252] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) 
[ 0.266256] io scheduler noop registered 
[ 0.266259] io scheduler anticipatory registered 
[ 0.266262] io scheduler deadline registered 
[ 0.266318] io scheduler cfq registered (default) 
[ 0.266474] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[ 0.266507] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[ 0.267027] ACPI: AC Adapter [AC] (on-line) 
[ 0.267138] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0 
[ 0.267547] ACPI: Lid Switch [LID] 
[ 0.267609] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1 
[ 0.267616] ACPI: Power Button [PBTN] 
[ 0.267680] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2 
[ 0.267685] ACPI: Sleep Button [SBTN] 
[ 0.268257] Marking TSC unstable due to TSC halts in idle 
[ 0.268311] processor LNXCPU:00: registered as cooling_device0 
[ 0.277222] Switching to clocksource acpi_pm 
[ 0.297797] thermal LNXTHERM:01: registered as thermal_zone0 
[ 0.297810] ACPI: Thermal Zone [THM] (31 C) 
[ 0.304272] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled 
[ 0.304373] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[ 0.304877] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[ 0.308142] isapnp: Scanning for PnP cards... 
[ 0.387723] ACPI: Battery Slot [BAT1] (battery absent) 
[ 0.387836] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5 
[ 0.387841] PCI: setting IRQ 5 as level-triggered 
[ 0.387848] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5 
[ 0.387861] serial 0000:00:1f.6: PCI INT B disabled 
[ 0.389303] brd: module loaded 
[ 0.389958] loop: module loaded 
[ 0.390097] input: Macintosh mouse button emulation as /devices/virtual/input/input3 
[ 0.390261] ata_piix 0000:00:1f.1: version 2.13 
[ 0.390275] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007) 
[ 0.390284] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11 
[ 0.390340] ata_piix 0000:00:1f.1: setting latency timer to 64 
[ 0.394998] scsi0 : ata_piix 
[ 0.400040] scsi1 : ata_piix 
[ 0.401181] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14 
[ 0.401186] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15 
[ 0.401723] Fixed MDIO Bus: probed 
[ 0.401785] PPP generic driver version 2.4.2 
[ 0.401864] tun: Universal TUN/TAP device driver, 1.6 
[ 0.401867] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[ 0.401982] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[ 0.402229] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11 
[ 0.402235] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11 
[ 0.402258] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[ 0.402263] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[ 0.402314] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1 
[ 0.402361] ehci_hcd 0000:00:1d.7: debug port 1 
[ 0.406235] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported 
[ 0.411142] ACPI: Battery Slot [BAT0] (battery present) 
[ 0.411156] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xfaeffc00 
[ 0.424543] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00 
[ 0.424708] usb usb1: configuration #1 chosen from 1 choice 
[ 0.424751] hub 1-0:1.0: USB hub found 
[ 0.424764] hub 1-0:1.0: 6 ports detected 
[ 0.424849] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[ 0.424871] uhci_hcd: USB Universal Host Controller Interface driver 
[ 0.424943] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11 
[ 0.424956] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[ 0.424961] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[ 0.425006] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 
[ 0.425032] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80 
[ 0.425144] usb usb2: configuration #1 chosen from 1 choice 
[ 0.425179] hub 2-0:1.0: USB hub found 
[ 0.425189] hub 2-0:1.0: 2 ports detected 
[ 0.425488] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11 
[ 0.425494] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11 
[ 0.425502] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[ 0.425507] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[ 0.425552] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3 
[ 0.425574] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40 
[ 0.425699] usb usb3: configuration #1 chosen from 1 choice 
[ 0.425737] hub 3-0:1.0: USB hub found 
[ 0.425746] hub 3-0:1.0: 2 ports detected 
[ 0.426000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11 
[ 0.426005] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11 
[ 0.426013] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[ 0.426018] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[ 0.426064] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4 
[ 0.426086] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20 
[ 0.426204] usb usb4: configuration #1 chosen from 1 choice 
[ 0.426238] hub 4-0:1.0: USB hub found 
[ 0.426248] hub 4-0:1.0: 2 ports detected 
[ 0.426381] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[ 0.436881] serio: i8042 KBD port at 0x60,0x64 irq 1 
[ 0.436896] serio: i8042 AUX port at 0x60,0x64 irq 12 
[ 0.437082] mice: PS/2 mouse device common for all mice 
[ 0.437320] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0 
[ 0.437339] rtc0: alarms up to one day, 114 bytes nvram 
[ 0.437506] device-mapper: uevent: version 1.0.3 
[ 0.437682] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email] 
[ 0.438762] device-mapper: multipath: version 1.1.0 loaded 
[ 0.438766] device-mapper: multipath round-robin: version 1.0.0 loaded 
[ 0.439848] EISA: Probing bus 0 at eisa.0 
[ 0.439882] EISA: Detected 0 cards. 
[ 0.441540] cpuidle: using governor ladder 
[ 0.441644] cpuidle: using governor menu 
[ 0.442212] TCP cubic registered 
[ 0.442437] NET: Registered protocol family 10 
[ 0.443033] lo: Disabled Privacy Extensions 
[ 0.443456] NET: Registered protocol family 17 
[ 0.444620] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4 
[ 0.568623] ata2.00: ATAPI: SAMSUNG CDRW/DVD SN-324S, U303, max UDMA/33 
[ 0.574586] Using IPI No-Shortcut mode 
[ 0.574747] PM: Resume from disk failed. 
[ 0.574764] registered taskstats version 1 
[ 0.575036] Magic number: 11:977:434 
[ 0.575171] rtc_cmos 00:06: setting system clock to 2011-05-15 14:25:54 UTC (1305469554) 
[ 0.575176] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[ 0.575179] EDD information not available. 
[ 0.584490] ata2.00: configured for UDMA/33 
[ 0.628069] ata1.00: ATA-6: FUJITSU MHT2040AH, 006C, max UDMA/100 
[ 0.628073] ata1.00: 78140160 sectors, multi 8: LBA 
[ 0.661186] ata1.00: configured for UDMA/100 
[ 0.803737] usb 1-1: new high speed USB device using ehci_hcd and address 2 
[ 0.983727] Freeing initrd memory: 7779k freed 
[ 1.034972] isapnp: No Plug & Play device found 
[ 1.035308] scsi 0:0:0:0: Direct-Access ATA FUJITSU MHT2040A 006C PQ: 0 ANSI: 5 
[ 1.035608] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[ 1.035886] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB) 
[ 1.035955] sd 0:0:0:0: [sda] Write Protect is off 
[ 1.035959] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[ 1.035995] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[ 1.036419] sda: 
[ 1.036612] scsi 1:0:0:0: CD-ROM SAMSUNG CDRW/DVD SN-324S U303 PQ: 0 ANSI: 5 
[ 1.036996] usb 1-1: configuration #1 chosen from 1 choice 
[ 1.037320] hub 1-1:1.0: USB hub found 
[ 1.037673] hub 1-1:1.0: 4 ports detected 
[ 1.039765] sr0: scsi3-mmc drive: 5x/24x writer cd/rw xa/form2 cdda tray 
[ 1.039769] Uniform CD-ROM driver Revision: 3.20 
[ 1.039893] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[ 1.039953] sr 1:0:0:0: Attached scsi generic sg1 type 5 
[ 1.060414] sda1 sda2 < sda5 > 
[ 1.096674] sd 0:0:0:0: [sda] Attached SCSI disk 
[ 1.096695] Freeing unused kernel memory: 664k freed 
[ 1.097254] Write protecting the kernel text: 4692k 
[ 1.097304] Write protecting the kernel read-only data: 1844k 
[ 1.118720] udev: starting version 151 
[ 1.308396] usb 1-1.1: new low speed USB device using ehci_hcd and address 3 
[ 1.404755] usb 1-1.1: configuration #1 chosen from 1 choice 
[ 1.437182] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI 
[ 1.437187] e100: Copyright(c) 1999-2006 Intel Corporation 
[ 1.437506] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11 
[ 1.437513] e100 0000:01:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11 
[ 1.460906] e100 0000:01:08.0: PME# disabled 
[ 1.468974] usbcore: registered new interface driver hiddev 
[ 1.470155] e100: eth0: e100_probe: addr 0xfcffd000, irq 11, MAC addr 00:11:43:41:d8:b8 
[ 1.470185] ohci1394 0000:01:01.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11 
[ 1.471505] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.1/1-1.1:1.0/input/input5 
[ 1.471641] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.7-1.1/input0 
[ 1.471670] usbcore: registered new interface driver usbhid 
[ 1.471674] usbhid: v2.6:USB HID core driver 
[ 1.524070] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11] MMIO=[fcfff800-fcffffff] Max Packet=[2048] IR/IT contexts=[4/8] 
[ 1.778654] EXT4-fs (sda1): mounted filesystem with ordered data mode 
[ 2.796221] ieee1394: Host added: ID:BUS[0-00:1023] GUID[364fc0003d3db830] 
[ 20.673010] udev: starting version 151 
[ 20.749495] Adding 1648632k swap on /dev/sda5. Priority:-1 extents:1 across:1648632k 
[ 20.975551] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input6 
[ 20.975638] ACPI: Video Device [VID] (multi-head: yes rom: no post: no) 
[ 20.975694] ACPI Warning for \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) (20090903/nspredef-433) 
[ 20.975786] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input7 
[ 20.975826] ACPI: Video Device [VID2] (multi-head: yes rom: no post: no) 
[ 21.140276] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[ 21.140318] Linux agpgart interface v0.103 
[ 21.172092] intel_rng: FWH not detected 
[ 21.422352] [drm] Initialized drm 1.1.0 20060810 
[ 21.434394] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2) 
[ 21.448747] parport_pc 00:0c: reported by Plug and Play ACPI 
[ 21.448819] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA] 
[ 21.466596] agpgart-intel 0000:00:00.0: Intel 855GM Chipset 
[ 21.467438] agpgart-intel 0000:00:00.0: detected 892K stolen memory 
[ 21.490527] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000 
[ 21.505125] type=1505 audit(1305469575.428:2): operation="profile_load" pid=559 name="/sbin/dhclient3" 
[ 21.506030] type=1505 audit(1305469575.428:3): operation="profile_load" pid=559 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[ 21.506538] type=1505 audit(1305469575.428:4): operation="profile_load" pid=559 name="/usr/lib/connman/scripts/dhclient-script" 
[ 21.527708] lib80211: common routines for IEEE802.11 drivers 
[ 21.527713] lib80211_crypt: registered algorithm 'NULL' 
[ 21.527723] dell-wmi: No known WMI GUID found 
[ 21.528109] lp: driver loaded but no devices found 
[ 21.536292] lp0: using parport0 (interrupt-driven). 
[ 21.577626] ppdev: user-space parallel port driver 
[ 21.600455] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8 
[ 21.602335] ieee80211: 802.11 data/management/control stack, git-1.1.13 
[ 21.602339] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com> 
[ 21.618830] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9 
[ 21.770229] i915 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11 
[ 21.770238] i915 0000:00:02.0: setting latency timer to 64 
[ 21.782593] [drm] set up 0M of stolen space 
[ 21.912579] yenta_cardbus 0000:01:01.0: CardBus bridge found [1028:0164] 
[ 21.912599] yenta_cardbus 0000:01:01.0: Using CSCINT to route CSC interrupts to PCI 
[ 21.912603] yenta_cardbus 0000:01:01.0: Routing CardBus interrupts to PCI 
[ 21.912610] yenta_cardbus 0000:01:01.0: TI: mfunc 0x012c1222, devctl 0x64 
[ 21.912711] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2 
[ 21.912715] ipw2100: Copyright(c) 2003-2006 Intel Corporation 
[ 21.974013] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[ 22.144575] yenta_cardbus 0000:01:01.0: ISA IRQ mask 0x0458, PCI irq 11 
[ 22.144582] yenta_cardbus 0000:01:01.0: Socket status: 30000086 
[ 22.144588] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #01 to #05 
[ 22.144599] yenta_cardbus 0000:01:01.0: pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff 
[ 22.144605] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xe000-0xefff: clean. 
[ 22.145297] yenta_cardbus 0000:01:01.0: pcmcia: parent PCI bridge Memory window: 0xfc000000 - 0xfdffffff 
[ 22.145302] yenta_cardbus 0000:01:01.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff 
[ 22.156679] ipw2100 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5 
[ 22.157254] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection 
[ 22.157273] ipw2100 0000:01:03.0: firmware: requesting ipw2100-1.3.fw 
[ 22.228467] [drm] initialized overlay support 
[ 22.542578] type=1505 audit(1305469576.464:5): operation="profile_load" pid=772 name="/usr/share/gdm/guest-session/Xsession" 
[ 22.570363] type=1505 audit(1305469576.492:6): operation="profile_replace" pid=773 name="/sbin/dhclient3" 
[ 22.571274] type=1505 audit(1305469576.492:7): operation="profile_replace" pid=773 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[ 22.571785] type=1505 audit(1305469576.492:8): operation="profile_replace" pid=773 name="/usr/lib/connman/scripts/dhclient-script" 
[ 22.620713] type=1505 audit(1305469576.544:9): operation="profile_load" pid=774 name="/usr/bin/evince" 
[ 22.624431] eth1: Radio is disabled by RF switch. 
[ 22.643565] type=1505 audit(1305469576.564:10): operation="profile_load" pid=774 name="/usr/bin/evince-previewer" 
[ 22.651039] type=1505 audit(1305469576.572:11): operation="profile_load" pid=774 name="/usr/bin/evince-thumbnailer" 
[ 22.841447] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean. 
[ 22.842296] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean. 
[ 22.842669] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean. 
[ 22.842735] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean. 
[ 22.843231] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean. 
[ 23.388327] fb0: inteldrmfb frame buffer device 
[ 23.388331] registered panic notifier 
[ 23.388342] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 
[ 23.388396] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5 
[ 23.388425] Intel ICH 0000:00:1f.5: setting latency timer to 64 
[ 23.398130] vga16fb: initializing 
[ 23.398136] vga16fb: mapped to 0xc00a0000 
[ 23.398143] vga16fb: not registering due to another framebuffer present 
[ 23.553311] Console: switching to colour frame buffer device 128x48 
[ 24.603295] intel8x0_measure_ac97_clock: measured 108635 usecs (5225 samples) 
[ 24.603300] intel8x0: clocking to 48000 
[ 25.027979] usbcore: registered new interface driver usbserial 
[ 25.028846] USB Serial support registered for generic 
[ 25.029457] usbcore: registered new interface driver usbserial_generic 
[ 25.029460] usbserial: USB Serial Driver core 
[ 2871.052079] usb 1-3: new high speed USB device using ehci_hcd and address 4 
[ 2871.186834] usb 1-3: configuration #1 chosen from 1 choice 
[ 2871.300903] Initializing USB Mass Storage driver... 
[ 2871.301057] scsi2 : SCSI emulation for USB Mass Storage devices 
[ 2871.301242] usbcore: registered new interface driver usb-storage 
[ 2871.301246] USB Mass Storage support registered. 
[ 2871.308811] usb-storage: device found at 4 
[ 2871.308816] usb-storage: waiting for device to settle before scanning 
[ 2876.308838] usb-storage: device scan complete 
[ 2876.309576] scsi 2:0:0:0: Direct-Access USB2.0 Flash Disk 2.10 PQ: 0 ANSI: 2 
[ 2876.315777] sd 2:0:0:0: Attached scsi generic sg2 type 0 
[ 2876.330559] sd 2:0:0:0: [sdb] 4124160 512-byte logical blocks: (2.11 GB/1.96 GiB) 
[ 2876.331049] sd 2:0:0:0: [sdb] Write Protect is off 
[ 2876.331054] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08 
[ 2876.331058] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[ 2876.334500] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[ 2876.334508] sdb: 
[ 2876.340751] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[ 2876.340758] sd 2:0:0:0: [sdb] Attached SCSI removable disk 
inspiron@Inspiron:~$ grep ipw

---

### Post by CCapslocKK on 2011-05-15
> **ngronewold said:**
> This issue with Dell Inspiron laptops was solved on the sticky thread at the top of the wireless advice section. There you will find directions on downloading packages via synaptic, but I think you'll need to be connected to the Internet via a land line.
 
Hi,
I didn't find the thread that youtalked about. Could you post here the link?
I don't know what i nor how work with the synaptic. The thread mentioned above explain that? I think that will be difficult, because at this time i don't have other way of connexion.

---

### Post by scorch1515 on 2011-05-15
Ok,

     I had this problem for the longest time on my Ubuntu and Linux Mint machines.  For me it was a driver issue, i think when you install Ubuntu it uses a "generic" driver for wifi, but when you try and mess with the drivers it deactivates the generic one.  Have you tried to install and drivers recently?  Anyway, you should install ndiswrapper and try to install the Windows drivers. Have fun!

---

### Post by CCapslocKK on 2011-05-15
Sorry, but how i do to install ndiswrapper and the windows drivers :confused:

---

### Post by mikewhatever on 2011-05-15
I think I found the problem in your dmesg output:
```
[ 22.624431] eth1: Radio is disabled by RF switch. 

```

That just says that the wireless is switched off, which can be verified with the following:
```
cat /sys/class/net/eth1/device/rf_kill
rfkill list all

```

I'd suggest trying Fn-f2 again just in case, as well as making sure wifi is enabled in the BIOS.

Next step:
```
rfkill unblock all
```

There is also a very old solution that you could try:
[http://ubuntuforums.org/archive/index.php/t-2586.html](http://ubuntuforums.org/archive/index.php/t-2586.html)

---

### Post by ngronewold on 2011-05-15
> **CCapslocKK said:**
> Hi,
I didn't find the thread that youtalked about. Could you post here the link?
I don't know what i nor how work with the synaptic. The thread mentioned above explain that? I think that will be difficult, because at this time i don't have other way of connexion.


Here's what I did -- It worked on 11.04 but it sounds like it may work for other installs:

- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot

Synaptic Package Manager is the program you need.  If you do a search through the system you should be able to find it and run it.  The two items listed above are included in the list.  And you need to be connected to the internet via LAN for this to work.  I hope this helps!

---

### Post by CCapslocKK on 2011-05-16
> **mikewhatever said:**
> I think I found the problem in your dmesg output:
```
[ 22.624431] eth1: Radio is disabled by RF switch. 

```
 
That just says that the wireless is switched off, which can be verified with the following:
```
cat /sys/class/net/eth1/device/rf_kill
rfkill list all

```
 
I'd suggest trying Fn-f2 again just in case, as well as making sure wifi is enabled in the BIOS.
 
Next step:
```
rfkill unblock all
```
 
There is also a very old solution that you could try:
[http://ubuntuforums.org/archive/index.php/t-2586.html](http://ubuntuforums.org/archive/index.php/t-2586.html)
 
Hi,
Here is the outputs:
 
 
inspiron@Inspiron:~$ cat /sys/class/net/eth1/device/rf_kill 
2 
inspiron@Inspiron:~$ rfkill list all 
inspiron@Inspiron:~$ rfkill unblock all 
[EMAIL="inspiron@Inspiron:~$"]inspiron@Inspiron:~$[/EMAIL] 
 
The keys Fn-F2 don't response anything. I've rebooted the machine but all remains the same thing. 
 
I think the wireless in enabled in the Bios because when i was windows some wifi network were detected.
 
Is it normal the 'rfkill list all' and 'rfkill unblock all' don't response anything?

---

### Post by CCapslocKK on 2011-05-16
> **ngronewold said:**
> Here's what I did -- It worked on 11.04 but it sounds like it may work for other installs:
 
- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot
 
Synaptic Package Manager is the program you need. If you do a search through the system you should be able to find it and run it. The two items listed above are included in the list. And you need to be connected to the internet via LAN for this to work. I hope this helps!
 
Thanks,
But at the moment i don't have another way of connexion. 
If another solution don't come, then i'll try to find another way of connection.

---

### Post by mikewhatever on 2011-05-16
How about this:
```
echo 0 | sudo tee /sys/class/net/eth1/device/rf_kill
```

It should change the value in /sys/class/net/eth1/device/rf_kill to 0.


> **ngronewold said:**
> Here's what I did -- It worked on 11.04 but it sounds like it may work for other installs:

- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot


That would have been useful if CCapslocKK had a Bradcom wireless card.

---

### Post by CCapslocKK on 2011-05-16
> **mikewhatever said:**
> How about this:
```
echo 0 | sudo tee /sys/class/net/eth1/device/rf_kill
```
 
It should change the value in /sys/class/net/eth1/device/rf_kill to 0.
 
Sorry, but what means this signal, like a bar, between "echo 0" and "sudo ..."???
They are two commands separely???

---

### Post by mikewhatever on 2011-05-17
> **CCapslocKK said:**
> Sorry, but what means this signal, like a bar, between "echo 0" and "sudo ..."???
They are two commands separely???

Technically, yes, those are two separate commands, but they should be run as one if you want it to work. The '|' symbol is a way of connecting commands. It's also called 'piping'. It's used a lot, and you can read a proper explanation in any bash tutorial, for example - [http://linuxcommand.org/lts0060.php#pipes](http://linuxcommand.org/lts0060.php#pipes).

---

### Post by CCapslocKK on 2011-05-17
> **mikewhatever said:**
> Technically, yes, those are two separate commands, but they should be run as one if you want it to work. The '|' symbol is a way of connecting commands. It's also called 'piping'. It's used a lot, and you can read a proper explanation in any bash tutorial, for example - [http://linuxcommand.org/lts0060.php#pipes](http://linuxcommand.org/lts0060.php#pipes).
 
Ok thanks,
The command is donne. But everything remains the same.
What i do now? Another test?
 
Now i´ll read the old solution at the link you've posted. Maybe it will be usefull...

---

### Post by CCapslocKK on 2011-05-17
Sorry,
I'd seen the link of the old solution, but i have no ideia of what means that: "All that was required was to add acpi_irq_isa=7 to the boot up parms in /boot/grub/menu.lst"
How i do that? could you explain to me? I'm very bad in informatics, and english too.

---

### Post by mikewhatever on 2011-05-17
OK, let's try that. There is not /boot/grub/menu.lst now, but there is /etc/default/grub instead.

Open the file for editing with the following (all one command):
```
gksudo gedit /etc/default/grub
```

You should see a file similar to this:
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="[COLOR="Red"]acpi_irq_isa=7[/COLOR]"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


Just add the 'acpi_irq_isa=7' boot option as shown in red above, then save and exit.
Last, run **sudo update-grub** and reboot.

---

### Post by ugm6hr on 2011-05-17
@mikewhatever: Is powersave mode at logout from Windows a possibility?
[http://support.microsoft.com/kb/910389](http://support.microsoft.com/kb/910389)
> If the network adapter supports a power management option, the following check box may be selected:
Allow the computer to turn off this device to save power
If the network adapter supports this option, it is available on the Power Management tab of the network adapter properties dialog box. To resolve this issue, disable this option on the Power Management tab.

---

### Post by CCapslocKK on 2011-05-17
> **mikewhatever said:**
> OK, let's try that. There is not /boot/grub/menu.lst now, but there is /etc/default/grub instead.
 
Open the file for editing with the following (all one command):
```
gksudo gedit /etc/default/grub
```
 
You should see a file similar to this:
 
 
Just add the 'acpi_irq_isa=7' boot option as shown in red above, then save and exit.
Last, run **sudo update-grub** and reboot.
 
Ok, i have donne exactly that, but all remains the same :(. Any idea?

---

### Post by joshuachoo on 2011-05-17
Try the following command:

[FONT=Courier New]rfkill list all[/FONT]

Does it say 'Soft blocked: Yes' under Wireless LAN?

If so, try the command:

[FONT=Courier New]rfkill unblock all[/FONT]

If your wireless is now working, then carry out the following:

[FONT=Courier New]sudo gedit /etc/rc.local[/FONT]

Add a single line above exit 0:

[FONT=Courier New]rfkill unblock all[/FONT]

Save the file, and reboot. Does WiFi work now?

---

### Post by CoolJohnB on 2011-05-18
> **ngronewold said:**
> Here's what I did -- It worked on 11.04 but it sounds like it may work for other installs:

- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot

Synaptic Package Manager is the program you need.  If you do a search through the system you should be able to find it and run it.  The two items listed above are included in the list.  And you need to be connected to the internet via LAN for this to work.  I hope this helps!

Thank you very much, this worked for me!  Great!:P

---

### Post by mikewhatever on 2011-05-18
> **CCapslocKK said:**
> Ok, i have donne exactly that, but all remains the same :(. Any idea?

Honestly, I am out of ideas. If you have Windows installed on that computer, do try what ugm6hr suggested above. Thinking forward, perhaps you should ask the mods to move this thread to the [Networking & Wireless Subforum]("http://ubuntuforums.org/forumdisplay.php?f=336") or open a new thread there.

---

### Post by CCapslocKK on 2011-05-18
> **mikewhatever said:**
> Honestly, I am out of ideas. If you have Windows installed on that computer, do try what ugm6hr suggested above. Thinking forward, perhaps you should ask the mods to move this thread to the [Networking & Wireless Subforum]("http://ubuntuforums.org/forumdisplay.php?f=336") or open a new thread there.
 
Any way thanks for your help.

---

### Post by CCapslocKK on 2011-05-18
> **joshuachoo said:**
> Try the following command:
 
[FONT=Courier New]rfkill list all[/FONT]
 
Does it say 'Soft blocked: Yes' under Wireless LAN?
 
If so, try the command:
 
[FONT=Courier New]rfkill unblock all[/FONT]
 
If your wireless is now working, then carry out the following:
 
[FONT=Courier New]sudo gedit /etc/rc.local[/FONT]
 
Add a single line above exit 0:
 
[FONT=Courier New]rfkill unblock all[/FONT]
 
Save the file, and reboot. Does WiFi work now?
 
Hi,
The command '[FONT=Courier New]rfkill list all'[/FONT]  don't response anything. Do you know why?
The command '[FONT=Courier New]rfkill unblock all'[/FONT]  didn't make my wifi working.

---

### Post by CCapslocKK on 2011-05-18
> **ugm6hr said:**
> @mikewhatever: Is powersave mode at logout from Windows a possibility?
[http://support.microsoft.com/kb/910389](http://support.microsoft.com/kb/910389)
 
The powersafe dialog box of my ubuntu hasn't this detail (if wifi is turnned off or not).

---

### Post by nm_geo on 2011-05-18
> **CCapslocKK said:**
> Hi,
The command '[FONT=Courier New]rfkill list all'[/FONT]  don't response anything. Do you know why?
The command '[FONT=Courier New]rfkill unblock all'[/FONT]  didn't make my wifi working.

I don't think rfkill comes pre-installed in Lucid 10.04. I just checked my history on my Lucid install and it says I installed it in January 2011.  Do you have a wired connection?  If so go to Synaptic and search for rfkill and install it. If it has been installed it will have a green box.

rfkill uses /dev/rfkill, which is present in Linux kernel 2.6.31 and later.

Check 

uname -a

Then run the commands.

---

### Post by ugm6hr on 2011-05-20
> **CCapslocKK said:**
> The powersafe dialog box of my ubuntu hasn't this detail (if wifi is turnned off or not).

This dialog box is on Windows. Is Windows still installed?

---

### Post by CCapslocKK on 2011-05-22
> **nm_geo said:**
> I don't think rfkill comes pre-installed in Lucid 10.04. I just checked my history on my Lucid install and it says I installed it in January 2011. Do you have a wired connection? If so go to Synaptic and search for rfkill and install it. If it has been installed it will have a green box.
 
rfkill uses /dev/rfkill, which is present in Linux kernel 2.6.31 and later.
 
Check 
 
uname -a
 
Then run the commands.
 
I've tryed a wired connection but my notebook didn't detect any connection. Thats strange :confused:. I don't have any idea. Maybe a problem when it was configurated to the 3G connection?

---

### Post by CCapslocKK on 2011-05-22
> **ugm6hr said:**
> This dialog box is on Windows. Is Windows still installed?
 
No, i don't have windows installled. :(

---

