---
title: "Beryl won't let me boot up"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by Afkpuz on 2007-07-14
Hey, I'm running ubuntu 7.04 with an ati x700 radeon mobility video card.  I installed beryl recently and had to change my video drivers to do so.  Then, I installed kiba dock.  Long story short, I cannot log in anymore.  I'll get to the login screen and type in my password and the system goes to terminal for a second, then takes me back to the login screen.  I also don't receive any error messages.  I've tried all the other session options and none allow me to get in.  Anyone know how to fix?  I'm thinking  that if I can uninstall beryl and kiba and switch back to the ati-restricted drivers, I'll be able to login.  Can anyone give the terminal code to do that?


I need the terminal code to:

1.) Uninstall Beryl
2.) Uninstall kiba dock
3.) Switch to ati-restricted drivers for x700 mobility



Thanks

---

### Post by luisromangz on 2007-07-14
If you didn't uninstall them, the ati propetary drivers are still present.

You only have to edit your /etc/X11/xorg.conf file (fron te command line, for exaple using vim) and replace the "ati" or "radeon" or the driver you are using now with the "fglrx" drivers.

You are able to use beryl with fglrx drivers, by using Xgl. This is the way I have Beryl running on my 200m card.

---

