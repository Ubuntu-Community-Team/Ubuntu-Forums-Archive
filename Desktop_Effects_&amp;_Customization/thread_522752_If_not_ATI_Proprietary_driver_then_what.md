---
title: "If not ATI Proprietary driver then what?"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by ipyakuza on 2007-08-11
Hello, from what i understand the ATI proprietary driver sucks.  I am running ubuntu 7.04 with KDE instead of gnome.  My goal is to setup compiz-fusion and my videocard is an ATI Radeon x850xt 256 AGP 8x.  I understand there are a few different ATI drivers: ati, radeon and fglrx.  I installed the ATI proprietary driver and it works with fglrx.  Unfortunatly i want a more stable x windows / compiz-fusion so I am trying to revert my driver back to the old one that comes with 7.04 (i hear it works perfect out of the box).  So, i ran the fglrx uninstall script and the ATI driver is no longer installed.  From here, what driver do i need to use and which one should be listed in my xorg.conf?  also what other options should i add to my xorg.conf to get xgl compiz working?  Thanks

---

### Post by Lolo Uila on 2007-10-14
You can run Beryl or Compiz with the fglrx driver if you are running under an XGL session.

If you want to run the default open-source ATI driver then see the following guides:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

And follow the steps for setting up the driver and xorg.conf.

Most of the info in that guide came from here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I ran an X800 XT PE both ways (open-source w/AIGLX & fglrx w/XGL) and it worked well in each configuration. The open-source route is easier and generally causes less problems and trouble-shooting headaches. However, I preferred the way video overlay was handled under XGL.

Your X850 XT should work well with the default open-source mesa driver. I had my X800 XT PE running Beryl on dual monitors with twin cubes and it was very fast. Only problem with dual monitors is you are limited to 2x 1024x768 resolution when using Beryl or Compiz. Something about the max texture size ( 2048x2048 ). Because of that limitation I have switched to an nVidia 7900GS card in my dual monitor system.

My other "game" box is running an ATI X1950 card on a 20" 1680x1050 monitor using the fglrx driver from the Ubuntu repositories and XGL (couldn't get any of the newer ATI drivers to work). I have both Compiz Fusion and the final build of Bery (0.3.0) installed and working well.

Good luck!

Aloha, Tim

---

