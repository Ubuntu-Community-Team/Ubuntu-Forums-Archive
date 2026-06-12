---
title: "Optiplex 775 and Radeon HD 2400 XT"
date: 2009-05-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by daehenoc on 2009-05-11
Hi all,

I've installed 9.04 on my Optiplex 775, which has a ATI (RV610) Radeon HD 2400 XT low profile PCI-E video card in it.

I've got two monitors attached and using the open source ATI driver, the big desktop works exactly how I want it.  (3840x1200 desktop, applications maximise to either the left screen or the right screen, I can drag applications from the left to the right monitor and vice versa, I have one set of panels on the left monitor with Applications, Places and System.)

But this driver doesn't provide the 3D capabilities of the fglrx driver, which I want for the Compiz stuff.

I have attempted to install the Ubuntu version of the fglrx driver as per the cchtml.com web site ([http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)) and I get no joy :(
I have installed the driver and use the command:
> sudo aticonfig --initial=dual-head --screen-layout=right
Which gives me two X screens with two sets of panels and I can't move windows between the two X screens.

No combination of screen-layout or dtop or overlay options work to give me the same layout as the open source driver (as per the Configuring page: [http://wiki.cchtml.com/index.php/Configuring]("http://wiki.cchtml.com/index.php/Configuring"))

Has anyone got the ATI driver (Ubuntu or ATI version) to work with dual screens the way I describe above, and with Compiz?  If so, can you post your xorg.conf file here please??

Thanks,
Greg

---

### Post by coffeeaddict22 on 2009-05-13
The proprietary driver also has a config program under Applications/Accessories/ that should do the trick.

---

