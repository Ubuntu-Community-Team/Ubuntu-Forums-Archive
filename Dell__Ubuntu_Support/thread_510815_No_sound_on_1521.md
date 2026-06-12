---
title: "No sound on 1521"
date: 2007-07-27
forum: Dell  Ubuntu Support
---

### Post by WoPr on 2007-07-27
Hi guys! 

Yesterday I posted a message on Dell forums, because the distro I was using was Debian 4.0, but I have already try with Ubuntu 6.06, 6.10 and 7.04 with no results. The message is as follows:


----- Msg. on Dell forums

Hi everybody!

Recently I have purchased many Inspiron 1521 for one of our customers, and now I have a very BIG problem. I could not get the audio device to work properly. I´m running Debian Etch with 2.4.18-4-686 and alsa driver v 1.0.14.rc4, but the sound does not work.

The dmesg for the audio section is as follows:

ALSA /etc/dell/alsa-driver-1.0.14rc4/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:558: hda_intel: azx_get_response timeout, switching to polling mode...
ALSA /etc/dell/alsa-driver-1.0.14rc4/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:564: hda_intel: azx_get_response timeout, switching to single_cmd mode...
hda_codec: No auto-config is available, default to model=ref
ALSA /etc/dell/alsa-driver-1.0.14rc4/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1020: hda-intel: no codecs initialized
ACPI: PCI interrupt for device 0000:00:14.2 disabled


The lspci is:

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia

And the lspci -vn and lspci -v

00:14.2 0403: 1002:4383
Subsystem: 1028:01fc
Flags: slow devsel, IRQ 193
Memory at febfc000 (64-bit, non-prefetchable) [disabled] [size=16K]
Capabilities: [50] Power Management version 2

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
Subsystem: Dell Unknown device 01fc
Flags: slow devsel, IRQ 193
Memory at febfc000 (64-bit, non-prefetchable) [disabled] [size=16K]
Capabilities: [50] Power Management version 2

The alsaconf script detects the hardware device, but still don`t work. Alsamixer throws:

alsamixer: function snd_ctl_open failed for default: No such device

I try to change the "model=" in /etc/modprobe.d/alsa-base with no result, and I need to have everything in the laptop ok for the next week...

Any ideas?

Thanks a lot and best regards,
Iker

----- End msg. Dell forums

Does anyone have the same issue?

Thanks a lot!!

---

### Post by WoPr on 2007-07-27
Hi all!

I try modifying teh file /etc/modprobe.d/alsa-base adding the option:

options snd-hda-intel probe_mask=10 

and the module loads OK. I can see the card in /proc/asound/cards but the alsa mixer does not recognize it...

Any ideas?

Thanks!

---

### Post by WoPr on 2007-07-28
Well!!

Fixed with kernel 2.6.17-10, ndiswrapper for wifi card and the latest ATI drivers for video. Everything is OK now.

Just left the integrated webcam!!!!

Best regards.

---

### Post by sqtz on 2007-07-30
Hi, 

Ok. Audio is working with 2.6.17-10 and model=ref.. but a lot of ACPI functions are lost. No suspend/hibernate, functions keys not working properly (lcd bright, suspend,etc), no powerbutton, and so... ACPI works much better with 2.6.20-16. Any idea ? best regards!

i opened a bug entry in launch pad but they mark it as "incomplete" .. help me if you can...

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128085](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128085)

(i'm the same from Dellcommunitty, yes) :-)

---

### Post by sqtz on 2007-08-04
**FIX HERE FOR FEISTY KERNEL:**

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128085](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/128085)

---

