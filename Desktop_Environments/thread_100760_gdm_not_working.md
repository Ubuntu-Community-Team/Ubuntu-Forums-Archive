---
title: "gdm not working"
date: 2005-12-08
forum: Desktop Environments
---

### Post by dhayes on 2005-12-08
Having problems using gdm, get a blank screen instead of a graphical login window (recovery mode text login is ok). Starting gdm or startx from prompt also results in blank screen.  So, I type:
sudo /etc/init.d/gdm stop
sudo apt-get remove gdm --purge

Note: here I can start kdm and open xfce and play around. This was good news it first, since I was playing for days with xorg.conf to see anything graphical. Probably an issue with using my Intel integrated 82845G graphics card. Anywy, having success with SOMETHING graphical, I login using kde. When I re-install:
sudo apt-get install gdm
sudo /etc/init.d/gdm start

I get the following:
invoke-rc.d: initscript gdm, action "reload" failed.

But am able to open a default ubuntu gnome desktop on :1 with xfce on :0.

On reboot, it's back to black screen. Again stopping gdm, removing, installing, then reconfiguring:

root@dhayes:~ # dpkg-reconfigure gdm
 * Reloading GNOME Display Manager configuration...  * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
Warning: the string include-menu-defs did not occur in template file /etc/X11/twm//system.twmrc-menu
Cannot open file /etc/X11/mwm//system.mwmrc-menu.

install-menu: /etc/menu-methods/motif-clients: aborting
update-menus[6298]: Script /etc/menu-methods/motif-clients returned error status 1.


What does all of this mean? I do have a workaround running an ubuntu gnome session from the kubuntu/kde/kdm login window, but would prefer to run gdm. Not everything works as it used to. 

Thank in advance for your help!
Cheers,
Dan

PS All of this came about after upgrading from 4.10 to 5.10, what a headache! My new mantra: "If it ain't broke don't break it."

---

