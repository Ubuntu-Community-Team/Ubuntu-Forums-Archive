---
title: "is there any possibilities to enable desktop effects in a generic video card"
date: 2008-01-29
forum: Desktop Effects &amp; Customization
---

### Post by boy bato on 2008-01-29
is there any possibilities to enable desktop effects in a generic video card identifier with a vesa driver????????


help,,,

---

### Post by overdrank on 2008-01-29
> **boy bato said:**
> is there any possibilities to enable desktop effects in a generic video card identifier with a vesa driver????????


help,,,

HI and can you give us more info on the graphics card with the command in the terminal ```
lspci
``` and look for VGA and post the output.

---

### Post by boy bato on 2008-01-29
[QUOTE=overdrank;4233312]HI and can you give us more info on the graphics card with the command in the terminal ```
lspci
``` and look for VGA and post the output.[/QUOin 



in lspci command it appears:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:0d.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

in vga it appears:

NON

---

### Post by FuturePilot on 2008-01-30
```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```
That's your graphics card. From what I've heard Compiz should work. Try
```
compiz --replace
``` in a terminal and see what happens.

---

### Post by boy bato on 2008-01-30
> **FuturePilot said:**
> ```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```
That's your graphics card. From what I've heard Compiz should work. Try
```
compiz --replace
``` in a terminal and see what happens.




the minimize,,restore and close button are gone when i run the compiz --replace,,,how should i get back those things

---

### Post by overdrank on 2008-01-30
> **boy bato said:**
> the minimize,,restore and close button are gone when i run the compiz --replace,,,how should i get back those things

HI you can use the command ```
metacity --replace
``` Also you may search synaptic manager for the 915 resolution and this may help.

---

### Post by Ub1476 on 2008-01-30
Note that you cannot use the "vesa" driver for anything else than failsafe, which means Compiz wont work on it. I think you should select the "i810" driver in System>Administration>Screens and Graphics.

You might have to restart X for it to work (save documents etc first):

```
<Control>+<Alt>+<Backspace>
```

The 915 resolution which can be found in Synaptic has helped many other as well.

---

