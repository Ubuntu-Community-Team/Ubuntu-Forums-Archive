---
title: "Can't Log In"
date: 2009-08-19
forum: Desktop Environments
---

### Post by mardukvmbc on 2009-08-19
Was asked to do a regular system update on Kubuntu Jaunty 64 bit and now can't log in.

I get the graphical greeter, put in my password, get a black screen for a second and then back to the login screen.

No errors that I can see.

Uninstalled my nvidia drivers and reinstalled with no effect. Reinstalled the kubuntu-desktop package also with no effect. nvidia-xconfig doesn't report any problems.

Interestingly, the greeter says welcome to localhost.localdomain instead of localhost which it used to say.

I have 4 different accounts and they all have the same problem. Logging in with the console yields no errors.

Please help!

---

### Post by krazyd on 2009-08-20
did you try logging in while the nvidia drivers were uninstalled?

---

### Post by mardukvmbc on 2009-08-20
you bet, just got a black screen.
also tried renaming my .kde folder so kde would recreate it, no joy.
Thanks very much for the quick response krazyd!

---

### Post by krazyd on 2009-08-20
Hmm.

Try this:

Try to log in, and once that fails and you get back to the login screen, press CTRL-ALT-F1 to go to tty1 and log in there.

Then type in ```
cat /var/log/Xorg.0.log | grep -C 4 '(EE)'
``` which should produce some output showing what's happening when you try to log in.

Does it give any clues?

---

### Post by mardukvmbc on 2009-08-20
ok, the errors listed:
canlt load firegl drm library (libfglrxdrm.so)
failed to load module "dri" (a required submodule could not be loaded, 0)
xkb: no components provided for device virtual core keyboard

looks like nvidia is working though, it loaded the module ok.
Thanks!

---

### Post by krazyd on 2009-08-20
Hang on! That error is showing that the xserver is trying to load the  proprietary ATI driver (fglrx).

Did you try to install the fglrx driver or an ATI card at some stage?

Anyway, run this command to reconfigure your xorg.conf. Hopefully this will get you back to your desktop and you can configure the nvidia drivers from there.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Edit: you might get asked a few questions. See here: [http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

---

### Post by mardukvmbc on 2009-08-20
thanks for the attempt; no joy.
Edit: I'm reinstalling after backing up... hopefully that works.

---

### Post by mardukvmbc on 2009-08-21
I've got it fixed now after a reinstall. Took only ~ 1 hr to get everything back up and working (left the /home mount where it was) so it was pretty quick.
Thanks for your help though, it's very much appreciated!:KS

---

