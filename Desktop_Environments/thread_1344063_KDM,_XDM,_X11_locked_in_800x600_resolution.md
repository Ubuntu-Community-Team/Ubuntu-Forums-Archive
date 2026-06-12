---
title: "KDM, XDM, X11 locked in 800x600 resolution"
date: 2009-12-02
forum: Desktop Environments
---

### Post by Lars Noodén on 2009-12-02
With today's update, KDM, XDM, and X11 seem locked in 800x600 resolution.  I've tried reconfiguring the xserver:

sudo dpkg-reconfigure xserver.org

Tried making a new /etc/X11/xorg.conf

Xorg -configure

And replacing kdm with xdm, but to no avail. 

I also tried wiping the kubuntu installation and doing a fresh install.  
The only choices offered by System Settings -> Display -> VGA1 are 800x600 and 640x480.  The resolution should be 1680x1050.  

The problem has been mentioned before, what is the way to slap ubuntu back into behaving?

---

