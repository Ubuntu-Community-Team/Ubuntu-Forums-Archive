---
title: "Dell D620 Trackpad sensitivity"
date: 2008-01-30
forum: Dell  Ubuntu Support
---

### Post by bendowling on 2008-01-30
I'm having a problem with 7.10 on my Dell D620. That model has both a trackpad and the 'nipple' pointer.
 Adjusting the system mouse preferences adjusts the preferences of the 'nipple' pointer, but I can't make any changes to the trackpad. 

As a result the trackpad sensitivity is really bad, and it takes me about 5 full drags to get from one side of the screen to the other! 

Any suggestions?

Thanks in advance, Ben

---

### Post by flippbonq on 2008-01-30
what do you have in /etc/X11/xorg.conf] for "InputDevice" sections and are you using a docking station or not? check to see what your settings are for /dev/psaux or /dev/input/mouse.

if you want you can try to use [qsynaptics](http://www.ubuntu1501.com/2007/04/configure-synaptic-touchpad-settngs.html) which only requires adding a few lines to your xorg.conf for extra gui config options. if you want to edit your own xorg.conf check this out : [d620 synaptic settings]("http://javier.rodriguez.org.mx/index.php/linux/debian-gnulinux-on-dell-d620"). there's also settings for  [ibook/macbook 2 finger scrolling in ubuntu](http://lucumr.pocoo.org/cogitations/2007/11/13/two-finger-scrolling-on-ubuntu/). ( like the ibook/macbook )

*added* don't forget to **backup** your xorg.conf before editing!

---

