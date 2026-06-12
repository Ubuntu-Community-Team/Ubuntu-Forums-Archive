---
title: "Unstable system, random crashes and freezes"
date: 2010-09-15
forum: Desktop Environments
---

### Post by guozhen on 2010-09-15
I'm quite new to ubuntu (only a few weeks) but I'm already in love with its features. I installed the 64-bit version on my newly built desktop but it frequently freezes and crashes. Sometimes it can go for several hours without crashing but other times it crashes on startup. I'm not sure if any particular application is causing this as its occurance is random. Firefox frequently crashes and sometimes applications refuse to open. As for my hardware it includes Asus M4A77TD, phenom II x4 955(3.2ghz), sapphire ati radeon 5750. Any help or suggestions would be very much appreciated. Thanks.

---

### Post by davidvandoren on 2010-09-18
open the terminal and 

run this command.Just copy and paste.
```
dmesg |grep BIOS
```

Many other people have a similar problem not only with Ubuntu.
I change from Fedora to Ubuntu because of this and Ubuntu runs On my PC more stable. Two freezes, some logout, and application crashes so far. However its endurable. 

This is what I got using Fedora
```
dmesg |grep BIOS
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 00000000bf780000 (usable)
 BIOS-e820: 00000000bf780000 - 00000000bf78e000 (ACPI data)
 BIOS-e820: 00000000bf78e000 - 00000000bf7d0000 (ACPI NVS)
 BIOS-e820: 00000000bf7d0000 - 00000000bf7e0000 (reserved)
 BIOS-e820: 00000000bf7ed000 - 00000000c0000000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
 BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
AMI BIOS detected: BIOS may corrupt low RAM, working around it.
  [COLOR="Red"]#3 [00000ff790 - 0000100000]    BIOS reserved ==> [00000ff790 - 0000100000]
  #5 [000009fc00 - 00000fdcc0]    BIOS reserved ==> [000009fc00 - 00000fdcc0]
  #6 [00000fde0c - 00000ff780]    BIOS reserved ==> [00000fde0c - 00000ff780][/COLOR]
PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
apm: BIOS not found.
hda_codec: ALC889: BIOS auto-probing.
```  


And this is now with Ubuntu which runs more stable.
```
dmesg |grep BIOS
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf780000 (usable)
[    0.000000]  BIOS-e820: 00000000bf780000 - 00000000bf78e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf78e000 - 00000000bf7d0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf7d0000 - 00000000bf7e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf7ed000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000]  [COLOR="red"] #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000][/COLOR]
[    0.526163] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.560737] PnPBIOS: Disabled by ACPI PNP
[    0.654498] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   12.313829] hda_codec: ALC889: BIOS auto-probing.

```
 Maybe the problems are related and hopefully someone can figure out What's wrong.
Maybe the ram?

---

### Post by guozhen on 2010-09-18
Thanks for replying, I entered the code and got this:

[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff90000 (usable)
[    0.000000]  BIOS-e820: 00000000cff90000 - 00000000cffa8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffa8000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #4 [000009ec00 - 0000100000]    BIOS reserved ==> [000009ec00 - 0000100000]
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    1.256681] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.839835] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.

---

### Post by davidvandoren on 2010-09-18
see if this thread can help you. Your Problems might have something to do with it.

[http://ubuntuforums.org/showthread.php?t=1018854]("http://ubuntuforums.org/showthread.php?t=1018854")

---

### Post by Ub28 on 2010-09-19
Have you tested for faulty hardware?

Maybe this could help: [http://www.overclockers.com/forums/showthread.php?t=335813](http://www.overclockers.com/forums/showthread.php?t=335813)

---

### Post by guozhen on 2010-09-19
I ran ran memtest 86 from a cd at startup and it found several million errors. I'm assuming this is my problem. Does this mean it's incompatible with my processor? I'm using 4gb of G.Skill ddr3 ram, it can be found here:
[http://www.canadacomputers.com/product_info.php?cPath=24_311_312_611&item_id=023354](http://www.canadacomputers.com/product_info.php?cPath=24_311_312_611&item_id=023354)
is it incompatible with amd processors or is the product just defective?

---

### Post by davidvandoren on 2010-09-19
Most likely it means that your memory is corrupted.

You will need to buy some new memory  (ram)

---

