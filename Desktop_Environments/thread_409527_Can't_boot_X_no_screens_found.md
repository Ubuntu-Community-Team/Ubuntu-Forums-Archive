---
title: "Can't boot X no screens found"
date: 2007-04-14
forum: Desktop Environments
---

### Post by Charles399 on 2007-04-14
Hi,

I installed Xubuntu with the alternate cd. It is a MMX 266mhz with 128 mo ram. The graphic card is a matrox mga  s3 1064SG. I tried the mga, s3 and de vga driver. I can login but X doesn't start.

I get this when I type *startx*  with the mga driver:

```
(WW) MGA: No matching Device section for instance (BusID PCI:0:19:0) found
(EE) No no device detected.

Fatal server error:
no screens found
XIO:   fatal IO 104 (Connection reset by peer) on X server ":0.0"
```


when I type *startx* with s3, I get:

```

(EE) s3(0): Cannot read V_BIOS (2 time)
(EE) s3(0): no valid modes found
(EE) Screen(s) found, but none have a usable configuretion

Fatal server error:
no screens found
XIO:   fatal IO 104 (Connection reset by peer) on X server ":0.0"


```
I tried sudo-dpkg-reconfigure xserver-xorg many time :( 

thanks,

ChArleS

---

### Post by PurplePenguin on 2007-04-14
Try sudo dpkg-reconfigure xserver-xorg one more time, but select "vesa" as your driver.

---

### Post by Charles399 on 2007-04-14
Thanks to answer so fast,

I have this error:

```

(WW) VESA: No matching Device section for instance (BusID PCI:0:19:0) found
(EE) VESA(0): Cannot read V_BIOS
(EE) Screen(s) found, but none have a usable configuretion

Fatal server error:
no screens found
XIO:   fatal IO 104 (Connection reset by peer) on X server ":0.0"

```

---

### Post by taurus on 2007-04-14
Try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Otherwise, post the output of this command here.

```
lspci
```

---

### Post by Charles399 on 2007-04-15
With *sudo dpkg-reconfigure -phigh xserver-xorg* I can change only the resolution. I get the same error with the V_BIOS. Is there an other command than *startx* or *reboot* to start X?

with *lspci*

```


00:00.0 Host bridge: Intel Corporation 430VX 82437VX TVX [TritonVX] (rev 02)
00:07.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II] (rev 01)
00:07.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:07.2 USB Controller: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II] (rev 01)
00:0b.0 VGA compatible controller: S3 Inc. 86c775/86c785 [Trio 64V2/TX or /GX (rev 16)
00:13.0 VGA compatible controller: Matrox Graphics, Inc. MGA 1064 [Mystique] (rev 3)

```

Charles

---

### Post by taurus on 2007-04-15
Do you happen to have an onboard graphic controller and a second graphic card on your machine?

---

### Post by Charles399 on 2007-04-15
Yes. If I plug the screen on the onboard graphic controller the screen is black like if it wasn't plug.

---

### Post by taurus on 2007-04-15
I assume you are using the addon graphic card.  Can you go into your BIOS and turn off the onboard graphic controller?  I think that is where the problem is.

---

### Post by Charles399 on 2007-04-15
My BIOS is old and I can't find the onboard graphic controler. There is an PCI IRQ tabs with IRQ- (3to 15). For each one, I can choose Legacy ISA or PCI/ISA PnP.

---

### Post by Charles399 on 2007-04-15
bump

---

### Post by Charles399 on 2007-04-16
Sorry for bumping again. There are so many posts!

---

### Post by leogibson on 2007-04-17
[http://ubuntuforums.org/showthread.php?p=2467503&posted=1#post2467503](http://ubuntuforums.org/showthread.php?p=2467503&posted=1#post2467503)

this is a problem for me as well, has been for weeks.  very annoying.

none of the suggestions in either forums are working for me.  followed them to the letter.  i guess its because im on a laptop and have an ati chip.  next buy will be intel no matter how poor it performs.

---

