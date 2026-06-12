---
title: "256 Color Mode"
date: 2010-10-16
forum: Desktop Environments
---

### Post by webusr1 on 2010-10-16
Hi All,
How can I change my Ubuntu 10.04 Desktop 32bit to run in 256 color mode? I Google around and found where you should be able to change change color depth from 24 bpp to 16 bpp in xorg.conf.  BUT I CAN'T EVEN FIND THE XORG.CONF file!!! Can anyone tell where it is located and if the listed suggestion is correct for Lucid 10.04? Thanks!

Here's what was suggested:
You can create a new xorg.conf by switching into a  virtual virtual console (Ctrl + Alt + (1-6)) and running sudo service  gdm stop. 

Then run Xorg -configure (yes, it should be Xorg, not  xorg). If you had an old xorg.conf file in /etc/X11/ you'd first back  that up by doing sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup. 

Then  move your newly created xorg.conf to /etc/X11/ by running sudo mv  xorg.conf.new /etc/X11/xorg.conf and restart gdm by running sudo service  gdm start. 

Then you can change the color depth in there by  finding the appropriate section and changing/adding whatever's in there  to DefaultDepth 16

---

