---
title: "Screen blacks out for just a moment"
date: 2007-05-19
forum: Desktop Environments
---

### Post by mlanza on 2007-05-19
This really isn't a big issue, just a slight annoyance.  Every time I boot up, after about 2 minutes the screen momentarily goes black and 2 seconds later reappears.  This occurs regularly.  Any ideas how this can be corrected?

---

### Post by heimo on 2007-05-19
No idea what it could be, but in case someone else has same problem, could you give us some more information.[LIST=1]
[*]Does it happen exactly once per boot, at around 2 minutes?
[*]Does it matter if you have logged in, or leave it at gsm/kdm login screen?
[*]What graphics card and monitor do you use?
[*]What Xorg driver do you use? nv, nvidia, ati, fglrx, i810, intel?
[*]Is it Ubuntu Feisty Fawn 7.04 (did it happen before)?[/LIST]Is there anything about it in log files?
```
/var/log/Xorg.0.log
/var/log/messages

```

---

### Post by mlanza on 2007-05-19
1. Does it happen exactly once per boot, at around 2 minutes?

Yes.  Exactly once per boot.  Not a big deal really since it doesn't really impact my work.

   2. Does it matter if you have logged in, or leave it at gsm/kdm login screen?

I automatically login without entering my password.

   3. What graphics card and monitor do you use?

All Dell equipment.  Monitor has model number on back: 1907FPc

   4. What Xorg driver do you use? nv, nvidia, ati, fglrx, i810, intel?

Linux rookie.  Just used defaults that Ubuntu set.

   5. Is it Ubuntu Feisty Fawn 7.04 (did it happen before)?

Using Ubuntu since v6.  Now on v7.  I think it did happen before.

I could send you my logs if you forward me your email address.

mlanza /AT/ comcast /DOT/ net

---

### Post by heimo on 2007-05-19
Ok, thanks for the extra info. Instead of sending logs to me, could you run this command, which will pipe your Xorg log and output any lines with WW, EE or LoadModule on them and post the output here. You can copy paste this to terminal - eg. highlight the line and middle-click on a terminal window. Thanks!

```
cat /var/log/Xorg.0.log | grep -E '\(WW\)|\(EE\)|LoadModule'
```

---

### Post by mlanza on 2007-05-21
Hereya go:

        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(II) LoadModule: "pcidata"
(II) LoadModule: "i2c"
(II) LoadModule: "ddc"
(II) LoadModule: "dri"
(II) LoadModule: "extmod"
(II) LoadModule: "freetype"
(II) LoadModule: "glx"
(II) LoadModule: "int10"
(II) LoadModule: "type1"
(II) LoadModule: "vbe"
(II) LoadModule: "i810"
(II) LoadModule: "kbd"
(II) LoadModule: "mouse"
(II) LoadModule: "wacom"
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(II) LoadModule: "int10"
(II) LoadModule: "vbe"
(II) LoadModule: "vgahw"
(II) LoadModule: "int10"
(II) LoadModule: "vm86"
(WW) I810(0): Bad V_BIOS checksum
(II) LoadModule: "int10"
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(WW) I810(0): Extended BIOS function 0x5f64 not supported.
(II) LoadModule: "ddc"
(II) LoadModule: "fb"
(II) LoadModule: "xaa"
(II) LoadModule: "ramdac"
(II) LoadModule: "shadow"
(II) LoadModule: "int10"
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(WW) I810(0): Extended BIOS function 0x5f28 not supported.
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

---

### Post by heimo on 2007-05-21
Couple lines which get my attention:
```
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
```
This looks familiar and I'm quite sure I've seen similar error before (you could search forums / google).

```
(WW) I810(0): Bad V_BIOS checksum
```
This one looks bad. Is it a laptop with Intel graphics? If it is, I'd search for BIOS upgrade on manufacturers website. Or if it's desktop, I'd probably search motherboard manufacturers website.

---

