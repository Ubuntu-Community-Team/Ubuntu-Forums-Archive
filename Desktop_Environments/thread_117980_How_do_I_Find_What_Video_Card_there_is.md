---
title: "How do I Find What Video Card there is"
date: 2006-01-15
forum: Desktop Environments
---

### Post by Sef on 2006-01-15
There is an old computer on which I installed Ubuntu; however, the only setting for the screen is 800 x 600 and it is too big.  I want to change it to like 1024 x 768.  Once I know that I can search for what to do to change the setting.

Question:

1) How do I find what video card there is in this machine?


Computer Specs:  600 MHz, 128 RAM

---

### Post by fourchannel on 2006-01-15
asides from taking the case apart and looking at the card? you might try ```
lspci
``` and see if you recognise a vendor name. Nvidia, S3, 3DFX, ATI, and so on... you might also try going to system preferences and looking at the device manager and see what it says.

---

### Post by RAOF on 2006-01-15
Well, you could try (from a console)
```
lspci | grep -i vga
```
lspci will list all the pci devices and give a bit of information about them.  The " | grep -i vga" part will pipe the output (|) through the program "grep", which will look for a line containing "vga" and print that out.

So, on my system, "lspci | grep -i vga" gives:
```
0000:05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
```

---

### Post by dcstar on 2006-01-15
[QUOTE=RAOF]Well, you could try (from a console)
```
lspci | grep -i vga
```
lspci will list all the pci devices and give a bit of information about them.  The " | grep -i vga" part will pipe the output (|) through the program "grep", which will look for a line containing "vga" and print that out.

So, on my system, "lspci | grep -i vga" gives:
```
0000:05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
```[/QUOTE]
lshw gives me a lot more info on my video hardware in the "*-display" section (how much is of use is another question.......)

---

