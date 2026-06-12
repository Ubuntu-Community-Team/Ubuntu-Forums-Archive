---
title: "eeePC dual monitor help"
date: 2008-02-06
forum: Desktop Environments
---

### Post by pedwards on 2008-02-06
howdy everybody, 
i just got my eeePC and full gnome ubuntu running, 
how can i get the dual monitors up and running?
any ideas?

-thx


edit:
hey , is there a standard apt that sets up dual monitors?

---

### Post by pytheas22 on 2008-02-06
Try the Screens and Graphics dialog under the System>>Administration menu in Gnome.  It should allow you to set up dual monitors, although depending on your situation it might not work too smoothly.  Note that Screens and Graphics has only existed since Ubuntu 7.10, so hopefully you're using the latest release.

Also if you happen to have an nvidia video card, you can run the program nvidia-settings in a terminal to configure your screens.

If this doesn't work, you might have to hack your /etc/X11/xorg.conf file manually.  There are directions online on how to set up dual monitors in such a way.  You will need to know what kind of video card(s) you have and some bus id numbers, among other things.

EDIT: keep in mind that before playing with your X settings, it's always a good idea to backup your current xorg.conf file somewhere so that you'll have a working configuration to default to if you mess up.

---

### Post by pedwards on 2008-02-07
thanks for your help, 
its users like you that make ubuntu such a success.

---

