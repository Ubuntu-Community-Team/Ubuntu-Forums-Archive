---
title: "dual monitors with Everex PC"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by lindberg.bill on 2007-11-10
Computer: Everex TC2502
Hard Drive Size:  80 GB  
System RAM:  512 MB  
Operating System: Ubuntu 7.10
Processor Type:  VIA C7-D Processor  
Processor - Clock Speed:  1.5 GHz  
Multimedia Drive:  DVD-ROM/CD-RW (combo)  
Monitor:  Compaq MV520 & GATEWAY VX700
Hard Drive Speed (RPM):  7200 RPM  
Graphics Type:  VIA UniChrome Pro IGP  
Memory Speed:  533MHz  
Parallel Port:  1 - Parallel port  
Product Dimensions (L x W x H):  14.65"H x 6.89"W x 15.98"D  
Serial Ports:  1 - Serial port  
USB Ports:  6 - USB 2.0 ports  


I have an integrated graphics card and two pci slots.  It appears that only one of these pci slots was ever inteded for use as the other is blocked off by an attached peice of metal (no screws) any how I plugged in my GF MX 4000 - 64 MB and hooked up a monitor to it and my integrated graphics card and logged on to the ubuntu forums.  I looked for the dual monitor stuff and thought I should try the xinerama.  Oh I should have mentioned that when I booted up the computer it said that there was an unknown pci and it was ignoring.  I have a couple of questions here.

1.  Can dual monitors be done with and integrated graphics card and a pci card?   I have set up dual monitors with dual head cards with not trouble at all, but never with a setup like this.

2.  If this can be done is there a specific tutorial for this?

3. Since the pci card needs nvidia driver, I think, can I use twinview?

I guess these dual monitor questions are tedious and booring, from what I read many people are tired if hearing about dual monitor problems.  If this is really the case I apologise in advance.  I destroyed my other computer because I couldn't stop messing with it and now I just have to get my dual moitors back.

---

### Post by lindberg.bill on 2007-11-10
VIA UniChrome Pro IGP Graphics is the integrated graphics card.
I really would love to know if this is just possible.  I'm still trying to figure out which is the best way to try.  It seems most methods are used when there is a dual head card or two cards such as agp and pci not integrated graphics and a pci card.  I tried the user interface provided by gutsy to no avail.

---

### Post by lindberg.bill on 2007-11-10
Ok I have the formerly non-working pci card working as the default card and using the nvidia restricted drivers looks great.  So now I know that both cards are capable of being used as a display device.  Now the question remains what if any method of dual monitor configuration will work with an integrated graphics card and an nvidia pci graphics card.

---

### Post by lindberg.bill on 2007-11-11
~$ lspci -x | grep VGA
00:0a.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

---

### Post by sanitycheck on 2007-11-17
I don't know if this will help, but are you using the openchrome driver?  Note that the openchrome driver is broken in Gutsy, but the fix is here:

[http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646)

I doubt you can use nVidia twinview unless you have 2 nVidia cards, but I may be wrong.

---

### Post by boondocks on 2008-01-03
> **lindberg.bill said:**
>  ... I have an integrated graphics card and two pci slots.  It appears that only one of these pci slots was ever inteded for use as the other is blocked off by an attached peice of metal (no screws) any how I plugged in my GF MX 4000 - 64 MB and hooked up a monitor to it and my integrated graphics card and logged on to the ubuntu forums.  I looked for the dual monitor stuff and thought I should try the xinerama.  Oh I should have mentioned that when I booted up the computer it said that there was an unknown pci and it was ignoring.  I have a couple of questions here. ...


lindberg.bill,
I installed a second PCI card into one of the 2 PCI slots in the Everex TC2502.
But the system would not even boot up.
It did not even show the Everex boot logo.
I had monitors attached to the integrated graphics card and the installed PCI video card.
The monitors come out of sleep mode but nothing shows up on the screen.
Did you experience this?

(Once I removed the second PCI card and powered up the PC, everything went back to normal.)

I have attached a picture of the motheboard.
Which PCI slot did you install your GF MX 4000 card in?  Was it 1 or 2?

---

