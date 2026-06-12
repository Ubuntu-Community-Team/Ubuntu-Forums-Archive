---
title: "Bluetooth signal problem"
date: 2016-10-25
forum: Fedora/RedHat and derivatives
---

### Post by Thee on 2016-10-25
Hi,

I've recently bought a new desktop computer (mini-pc). I'm running Fedora 24 (Kernel 4.7.9-200, Gnome) and I have an Intel 7265 Wireless/Bluetooth card [(link)]("https://www-ssl.intel.com/content/www/us/en/wireless-products/dual-band-wireless-ac-7265.html")

Wireless works, but I'm having problems with bluetooth signal (at least I think that's the problem).

When I enable bluetooth, it doesn't find my (android) smartphone nor my headset (both are about 0,5m away from the computer), but it does see my SmartTV. Which is just above my computer.
My smartphone also doesn't see my computer, until I put it really close to the computer, like almost on top of the computer.
Then I can pair them without problems, but that's about it, sending files returns an error on the phone, and receiving also doesn't work (with no apparent error messages). Connectivity is lost when I move the phone further away.
It's the same with the headset, it connects and pairs only when I put them very close to the computer. After that I can hear sound on the headset, but as soon as I move them, sound shutters, lags, BT connection drops...

What I've already tried:
- connected my phone/headset; TV/headset to make sure everything works and it works fine.
- Installed Blueman, which yield almost same results (the range was slightly better). 
- checked if BT is hard/soft blocked and there's no problem there.
- ran ubuntu-live and checked if there's any difference (same problem there); I don't have Windows, so I can't test it.

Anyone has any ideas on this? Thanks.

Some more info:

```

$ dmesg | grep -i blue
[    3.773173] Bluetooth: Core ver 2.21
[    3.773185] Bluetooth: HCI device and connection manager initialized
[    3.773187] Bluetooth: HCI socket layer initialized
[    3.773189] Bluetooth: L2CAP socket layer initialized
[    3.773194] Bluetooth: SCO socket layer initialized
[    3.782428] Bluetooth: HCI UART driver ver 2.3
[    3.782430] Bluetooth: HCI UART protocol H4 registered
[    3.782431] Bluetooth: HCI UART protocol BCSP registered
[    3.782432] Bluetooth: HCI UART protocol LL registered
[    3.782433] Bluetooth: HCI UART protocol ATH3K registered
[    3.782433] Bluetooth: HCI UART protocol Three-wire (H5) registered
[    3.782455] Bluetooth: HCI UART protocol Intel registered
[    3.782465] Bluetooth: HCI UART protocol BCM registered
[    3.782466] Bluetooth: HCI UART protocol QCA registered
[    3.782467] Bluetooth: HCI UART protocol AG6XX registered
[    3.803433] Bluetooth: hci0: read Intel version: 370810011003110e25
[    3.803436] Bluetooth: hci0: Intel device is already patched. patch num: 25
[    5.668644] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.668646] Bluetooth: BNEP filters: protocol multicast
[    5.668648] Bluetooth: BNEP socket layer initialized
[   10.255351] Bluetooth: RFCOMM TTY layer initialized
[   10.255356] Bluetooth: RFCOMM socket layer initialized
[   10.255387] Bluetooth: RFCOMM ver 1.11

```

```

$ hciconfig -a hci0
hci0:    Type: Primary  Bus: USB
    BD Address: A4:02:B9:58:37:B0  ACL MTU: 1021:5  SCO MTU: 96:6
    UP RUNNING PSCAN 
    RX bytes:775 acl:0 sco:0 events:61 errors:0
    TX bytes:3535 acl:0 sco:0 commands:61 errors:0
    Features: 0xff 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'cirrus7'
    Class: 0x0c0104
    Service Classes: Rendering, Capturing
    Device Class: Computer, Desktop workstation
    HCI Version: 4.2 (0x8)  Revision: 0x1000
    LMP Version: 4.2 (0x8)  Subversion: 0x1000
    Manufacturer: Intel Corp. (2)

```

---

### Post by Thee on 2016-10-25
Ok, I'm an idiot :) I didn't attach the antennas that I got with the pc, which I assumed weren't needed for wifi only (which I tested, but don't use) and not for bluetooth, but obviously I was wrong. With the antennas attached, bluetooth works perfectly.
I've spent days searching the net for the answer and only after I've already posted a question here, I remember about the antennas and decide to try them out :) well, live and learn.

Problem solved. Thanks and sorry for the confusion.

---

