---
title: "ATI TV Wonder Pro"
date: 2006-06-04
forum: Desktop Environments
---

### Post by peppermg on 2006-06-04
I have an ATI TV Wonder Pro, and for the life of me I can't get it to work. I'm pretty sure its being loaded correctly.

Jun  4 11:37:17 pepbox kernel: [4294690.223000] cx2388x v4l2 driver version 0.0.5 loaded
Jun  4 11:37:17 pepbox kernel: [4294690.224000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 201
Jun  4 11:37:17 pepbox kernel: [4294690.224000] CORE cx88[0]: subsystem: 1002:00f8, board: ATI TV Wonder Pro [card=4,autodetected]
Jun  4 11:37:17 pepbox kernel: [4294690.224000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
Jun  4 11:37:17 pepbox kernel: [4294690.469000] cx88[0]/0: found at 0000:00:0b.0, rev: 5, irq: 201, latency: 32, mmio: 0xde000000
Jun  4 11:37:17 pepbox kernel: [4294690.537000] tuner 1-0060: All bytes are equal. It is not a TEA5767
Jun  4 11:37:17 pepbox kernel: [4294690.537000] tuner 1-0060: chip found @ 0xc0 (cx88[0])
Jun  4 11:37:17 pepbox kernel: [4294690.537000] tuner 1-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
Jun  4 11:37:17 pepbox kernel: [4294690.585000] tda9887 1-0043: chip found @ 0x86 (cx88[0])
Jun  4 11:37:17 pepbox kernel: [4294690.590000] cx88[0]/0: registered device video0 [v4l2]
Jun  4 11:37:17 pepbox kernel: [4294690.590000] cx88[0]/0: registered device vbi0

When I try to run tvtime I get this:
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/pepper/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

xawtv:
This is xawtv-3.94, running on Linux/i686 (2.6.15-23-386)
WARNING: Your X-Server has no DGA support.
/dev/video0 [v4l2]: ioctl VIDIOC_G_FBUF: Invalid argument
v4l-conf had some trouble, trying to continue anyway
ioctl: VIDIOC_G_FBUF(capability=0x0 [];flags=0x0 [];base=(nil);fmt.width=0;fmt.height=0;fmt.pixelformat=0x00000000 [....];fmt.field=ANY;fmt.bytesperline=0;fmt.sizeimage=0;fmt.colorspace=unknown;fmt.priv=0): Invalid argument

Any Ideas?

---

