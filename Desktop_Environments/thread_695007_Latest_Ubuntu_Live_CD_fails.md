---
title: "Latest Ubuntu Live CD fails"
date: 2008-02-12
forum: Desktop Environments
---

### Post by DoubleEweAreEx on 2008-02-12
Hi 
I have a limited experience with Linux and decided I wanted to install Linux onto a USB HDD I have.
I unplugged my 2 SATA drives on my desktop and attached the USB HDD.
I requested the latest Ubuntu x86 Live CD and am trying to use that.

It gives the Grub menu, I choose the Runlive/Install option and it begins to boot.
It sits at the horizontal bar for a while and then progresses to a standard type Linux boot display.
It gets about 4 lines down and just sites there.

The PC is still responsive, CAPS and NUMLOCK lights respond.
If I press CTRL ALT DEL it aborts what ever it is trying to do and starts to shut down.

Is it possible that it doesnt like my hardware? Its a fairly new box.
DDR3 Ram, quadcore cpu, NVidia GTS 8800, IDE CDROM and a USB2 HDD

Thanks in advance:)

---

### Post by overdrank on 2008-02-12
> **DoubleEweAreEx said:**
> Hi 
I have a limited experience with Linux and decided I wanted to install Linux onto a USB HDD I have.
I unplugged my 2 SATA drives on my desktop and attached the USB HDD.
I requested the latest Ubuntu x86 Live CD and am trying to use that.

It gives the Grub menu, I choose the Runlive/Install option and it begins to boot.
It sits at the horizontal bar for a while and then progresses to a standard type Linux boot display.
It gets about 4 lines down and just sites there.

The PC is still responsive, CAPS and NUMLOCK lights respond.
If I press CTRL ALT DEL it aborts what ever it is trying to do and starts to shut down.

Is it possible that it doesnt like my hardware? Its a fairly new box.
DDR3 Ram, quadcore cpu, NVidia GTS 8800, IDE CDROM and a USB2 HDD

Thanks in advance:)

Hi and welcome, you can try and when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add vga=771 or 775 before the -- then press enter. This will allow you to see any errors while booting and hopefully bring you to the live cd. Hope this helps and good luck!

---

