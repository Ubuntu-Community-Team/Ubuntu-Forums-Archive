---
title: "Dymo CoStar 320 Breezy 5.10 no luck with USB"
date: 2006-02-21
forum: Desktop Environments
---

### Post by raptor.ghost on 2006-02-21
Hi Fellow Ubuntu's

I have recent pick up this with Linux and are having alot of fun converting all my machines at home and some at my work (without my boss knowing about it) ;o)

I have allready succesfully installed Breezy 5.10 on a IBM Thinkpad T22, T23, T30 and a IBM Netvista M42.

I have all the stuff running that I need, network, applications, Internet and using Wine/DVDShrink for my 'dvd' work.

I also have a Canon 5200 and that I can use with TurboPrint, cost by it will work, i think.

Now to my only problem, Dymo-CoStar 320 Labelwriter....hmmm

I have found that Cups and using pbm2lwxl will work but my dymo will not accept any printing (just sitting in the spoolque and do nothing) and i stumble on this, regarding USB...


[http://www.linuxprinting.org/show_printer.cgi?recnum=Dymo-CoStar-LabelWriter_XL](http://www.linuxprinting.org/show_printer.cgi?recnum=Dymo-CoStar-LabelWriter_XL)

[I]" One annoying thig is that you need to patch the USB printer driver (and
also the USB controller driver in Linux 2.6). This is because Dymo uses a
USB low speed interface in bulk transfer mode, which isn't allowed by the USB
standard.

diff ../../linux-2.6.9-orig-fedora-core-3/drivers/usb/host/uhci-hcd.c uhci-hcd.c
1153c1153
<       if (urb->dev->speed == USB_SPEED_LOW)
---
> /*    if (urb->dev->speed == USB_SPEED_LOW)
1155c1155
< 
---
> */

$ diff ../../linux-2.6.9-orig-fedora-core-3/drivers/usb/class/usblp.c usblp.c
1009d1008
< 
1022c1021
<                       if ((epd->bmAttributes&USB_ENDPOINT_XFERTYPE_MASK)!=
---
> /*                    if ((epd->bmAttributes&USB_ENDPOINT_XFERTYPE_MASK)!=
1024a1024
> */[/I]

Could any one kind person help me how I could track down if this is my problem I having with the Dymo-CoStar printer I would be a happy person :D 

Thanks alot, Robert.

---

