---
title: "Touchpad stops working after typing"
date: 2012-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ad2476 on 2012-08-21
I'm on Ubuntu 12.04 64-bit on a Dell M1330. I've been having issues with the keyboard, touchpad and media buttons. Between 1 and 10 seconds after I start typing something, the webcam light will blink and the touchpad stops working. From then on, the media buttons won't work at all. I can get the touchpad working by clicking it frantically for a few seconds, but it's a real hassle.

Additionally, if I am typing a long piece (like this post), the CD drive will make a noise, the webcam flashes, and the keyboard and touchpad both will stop working for a period of time.

I've looked through other forum posts, and haven't seen anything quite like this. Some suggest to uncheck "Disable touchpad while typing", but that has had no effect.

Here is the dmesg from one such incident:

```
[  546.932608] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input21
[  547.827428] usb 2-6: USB disconnect, device number 19
[  549.708282] usb 2-6: new high-speed USB device number 20 using ehci_hcd
[  549.846543] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[  549.847016] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[  549.847873] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input22
[  553.420119] usb 2-6: USB disconnect, device number 20
[  559.220226] usb 2-6: new high-speed USB device number 21 using ehci_hcd
[  559.359028] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[  559.359516] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[  559.360628] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input23
[  567.152132] usb 2-6: USB disconnect, device number 21
[  569.863000] ACPI Error: Method parse/execution failed [\SMI_] (Node ffff8800ba22d528), AE_AML_INFINITE_LOOP (20110623/psparse-536)
[  569.863015] ACPI Error: Method parse/execution failed [\PWRE] (Node ffff8800ba22dde8), AE_AML_INFINITE_LOOP (20110623/psparse-536)
[  569.863023] ACPI Error: Method parse/execution failed [\NEVT] (Node ffff8800ba22dd70), AE_AML_INFINITE_LOOP (20110623/psparse-536)
[  569.863030] ACPI Error: Method parse/execution failed [\_GPE._L1C] (Node ffff8800ba22df00), AE_AML_INFINITE_LOOP (20110623/psparse-536)
[  569.863042] ACPI Exception: AE_AML_INFINITE_LOOP, while evaluating GPE method [_L1C] (20110623/evgpe-560)
[  607.633119] psmouse serio1: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
```

Edit: Just to clarify, this doesn't seem to happen on the Live CD or in Windows (I have dual-boot). It also comes and goes, the last time this problem occurred was April.

---

### Post by ad2476 on 2012-08-21
Well, it turns out that there wasn't really a software problem. Rather, a cable connecting the keyboard to the motherboard was loose, and whenever I typed, it would lose contact. The kernel would see this, as shown in: > [  547.827428] usb 2-6: USB disconnect, device number 19
[  549.708282] usb 2-6: new high-speed USB device number 20 using ehci_hcd and try and reload everything (which explains the flashing webcam, unresponsive touchpad, and CD drive noise).

If anyone happens to get this problem, and have exhausted all other options, try wiggling the keyboard cable. Just make sure you know what you're doing.

---

