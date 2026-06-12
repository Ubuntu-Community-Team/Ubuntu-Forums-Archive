---
title: "Display is gone"
date: 2009-09-15
forum: Desktop Environments
---

### Post by kierpaul on 2009-09-15
Can anyone help me here? I installed the new driver for Nvidia 185xx right from the directions on their website and after reboot I have no login screen or nothing. I can boot into recovery mode where I tried a "sudo gedit /etc/x11/x.org.conf" of my X.org.conf file but it errored out with a gtk display error. When I tried "sudo /etc/init.d/gdm start" I get a blank screen and nothing again. Any help is greatly appreciated. This all started with graphics problems on my Geforce 128 MB Nvidia card. I am running a 865 P4 32bit system on Jaunty. Thanks in advance!

Joe

---

### Post by dawynn on 2009-09-15
Ok -- you have a command line that you can use.  Great!  That's a good start.

For editing your xorg.conf (note -- not x.org.conf) from a command line, you will need to use a terminal-based editor.  gedit is a gui-based editor -- it won't help you here.  vi and emacs are the classic standards, but they have a steep learning curve.  I personally prefer jed, but likely its not on your system.  You can try...

sudo apt-get install jed

Once its installed, try...

sudo jed /etc/X11/xorg.conf

Use f10 to access the menus, everything else is fairly self-explanatory.

---

### Post by kierpaul on 2009-09-15
O.K., I will have to wait until I get home from work to try this. Thank you and all help is appreciated.

---

### Post by kierpaul on 2009-09-15
I got it to boot up to Desktop using this fellow's method [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A). Very good! Thank you for all of your help everyone!

---

