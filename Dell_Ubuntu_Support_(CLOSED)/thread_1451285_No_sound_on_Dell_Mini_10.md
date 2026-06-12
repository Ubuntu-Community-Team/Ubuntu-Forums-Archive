---
title: "No sound on Dell Mini 10"
date: 2010-04-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by legoman666 on 2010-04-10
Weirdly enough the little Ubuntu startup sound can still be heard when booting. But once I log in, I get no sound. The volume is not low and is not muted. I've tried youtube, mplayer etc. Regardless of the source, I get nothing.

Also, it used to work. Then something changed (nothing I did, I don't think) and now it doesn't.

LSPCI as follows: 
lspci
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

Come to think of it, it might have something to do with a Poulsbo driver package I installed in order to get decent support for the GMA500 video. (But I don't know enough to fix it)

Any ideas?

---

### Post by mikewhatever on 2010-04-10
Can you post the output of the following commands:

dmesg | grep -i hda

grep -i hda /var/log/syslog

---

### Post by legoman666 on 2010-04-10
dmesg | grep -i hda
[39891.916542] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
[39891.916555] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[39891.916567] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[39892.104313] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[39892.104335] HDA Intel 0000:00:1b.0: setting latency timer to 64
[41169.320405] HDA Intel 0000:00:1b.0: PCI INT A disabled
[41169.748539] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
[41169.748553] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[41169.748566] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[41169.936311] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[41169.936334] HDA Intel 0000:00:1b.0: setting latency timer to 64
[49888.276390] HDA Intel 0000:00:1b.0: PCI INT A disabled
[49888.704540] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
[49888.704553] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[49888.704566] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[49888.892310] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[49888.892332] HDA Intel 0000:00:1b.0: setting latency timer to 64
[51266.416389] HDA Intel 0000:00:1b.0: PCI INT A disabled
[51266.844545] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
[51266.844558] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[51266.844571] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[51267.032313] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[51267.032334] HDA Intel 0000:00:1b.0: setting latency timer to 64
[51677.428455] HDA Intel 0000:00:1b.0: PCI INT A disabled
[51677.856545] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
[51677.856559] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[51677.856571] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[51678.044314] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[51678.044335] HDA Intel 0000:00:1b.0: setting latency timer to 64
[51751.436385] HDA Intel 0000:00:1b.0: PCI INT A disabled
[51751.864539] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
[51751.864552] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[51751.864565] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[51752.052312] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[51752.052334] HDA Intel 0000:00:1b.0: setting latency timer to 64
[52266.996406] HDA Intel 0000:00:1b.0: PCI INT A disabled
[52267.424537] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
[52267.424550] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[52267.424563] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[52267.612313] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[52267.612335] HDA Intel 0000:00:1b.0: setting latency timer to 64
[123627.600386] HDA Intel 0000:00:1b.0: PCI INT A disabled
[123628.028539] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
[123628.028552] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[123628.028565] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[123628.216314] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[123628.216336] HDA Intel 0000:00:1b.0: setting latency timer to 64
[133495.564387] HDA Intel 0000:00:1b.0: PCI INT A disabled
[133495.992537] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
[133495.992550] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[133495.992562] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[133496.180311] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[133496.180333] HDA Intel 0000:00:1b.0: setting latency timer to 64


grep -i hda /var/log/syslog
Apr 10 11:27:58 Keira kernel: [123627.600386] HDA Intel 0000:00:1b.0: PCI INT A disabled
Apr 10 11:27:58 Keira kernel: [123628.028539] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
Apr 10 11:27:58 Keira kernel: [123628.028552] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Apr 10 11:27:58 Keira kernel: [123628.028565] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Apr 10 11:27:58 Keira kernel: [123628.216314] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr 10 11:27:58 Keira kernel: [123628.216336] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr 10 14:57:09 Keira kernel: [133495.564387] HDA Intel 0000:00:1b.0: PCI INT A disabled
Apr 10 14:57:09 Keira kernel: [133495.992537] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
Apr 10 14:57:09 Keira kernel: [133495.992550] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Apr 10 14:57:09 Keira kernel: [133495.992562] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Apr 10 14:57:09 Keira kernel: [133496.180311] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr 10 14:57:09 Keira kernel: [133496.180333] HDA Intel 0000:00:1b.0: setting latency timer to 64

Thanks for replying.

---

### Post by Timoteo32 on 2010-04-10
I have a Dell Inspiron laptop and I'm having a similar problem. It'll happen every few weeks. It seems like it's just the sound from the internet tho. No sound in Firefox or Chrome.  I can play podcasts in Movie Player fine....

---

### Post by theozzlives on 2010-04-10
Are you using the Moblin Remix? That was made for the Mini 10.

---

### Post by legoman666 on 2010-04-11
> **theozzlives said:**
> Are you using the Moblin Remix? That was made for the Mini 10.

I don't think so.

---

### Post by mikewhatever on 2010-04-11
Are you running Ubuntu? Which release? How about <cat /etc/lsb-release>?

---

### Post by legoman666 on 2010-04-11
> **mikewhatever said:**
> Are you running Ubuntu? Which release? How about <cat /etc/lsb-release>?

Ubuntu netbook remix.

---

### Post by mikewhatever on 2010-04-11
Can you actually post the output of the following:

cat /etc/lsb-release

---

### Post by legoman666 on 2010-04-11
> **mikewhatever said:**
> Can you actually post the output of the following:

cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

---

### Post by mikewhatever on 2010-04-11
Thanks. You don't seem to have the same sound problem I've had a few months back. [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/521775](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/521775)
Run 'aplay -l', to make sure the sound card is working (you should get something like the following):

```
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Then launch 'gstreamer-properties' and try to set the 'Output' to something other then default.

---

### Post by legoman666 on 2010-04-11
Thanks for the help so far mate.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

When I  was trying to test the different devices, it told me something was in use by  another open program. I rebooted and now my sound magically works. No idea what I did.

---

