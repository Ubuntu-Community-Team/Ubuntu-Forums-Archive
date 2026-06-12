---
title: "Wifi and Other WMs in Xubuntu?"
date: 2010-01-07
forum: Desktop Environments
---

### Post by imag1narynumber on 2010-01-07
I installed Xubuntu 9.10 on my notebook, and I'd like to run PekWM and/or Xmonad on it.  But how would I connect to wifi, either home or out and about?  I typically find wicd used in other distros, but I can't figure out what app Xubuntu uses as a wifi-connection gui.  So what would I run in Xmonad?  And if I do install wicd, I don't want that to screw up what Xubuntu already uses, since that's how I've got my woman set up on the machine.  Thanks for your help.

---

### Post by Jose Catre-Vandis on 2010-01-07
Your connection manager should be the same, it is installed, regardless of the WM/DE you use. You may have to invoke it through the terminal though, or write a script, depending on how your alternate DM/WM handles menus and installed programs

---

### Post by imag1narynumber on 2010-01-07
> **Jose Catre-Vandis said:**
> Your connection manager should be the same, it is installed, regardless of the WM/DE you use. You may have to invoke it through the terminal though, or write a script, depending on how your alternate DM/WM handles menus and installed programs

Yes, but what is the name of the manager in Xubuntu?  Put another way, what would I "invoke" through dmenu in Xmonad?

---

### Post by Jose Catre-Vandis on 2010-01-07
Have you tried loading a different WM/DE?

If so, check your **ifconfig** in a terminal. If nothing then its not happening automatically. Post output here.  If something, try a ping or loading a website. If that doesn't work, post output here.

EDIT

Have just installed openbox on my Jaunty Xubuntu 9.04 setup. Logged out, logged in again with Openbox, connected to network/internet automatically - in fact this happens before you login!

---

### Post by imag1narynumber on 2010-01-07
> **Jose Catre-Vandis said:**
> Have you tried loading a different WM/DE?

If so, check your **ifconfig** in a terminal. If nothing then its not happening automatically. Post output here.  If something, try a ping or loading a website. If that doesn't work, post output here.

EDIT

Have just installed openbox on my Jaunty Xubuntu 9.04 setup. Logged out, logged in again with Openbox, connected to network/internet automatically - in fact this happens before you login!

I've installed PekWM, fluxbox, awesome3, and Xmonad. Nothing magical happens.  I can only assume your wifi has no WPA2 or anything of the sort.

---

### Post by XubuRoxMySox on 2010-01-07
Xubuntu ships with the Gnome network manager. You can add the Network Manager Applet to a panel on your desktop and configure it from there. Wicd should work fine if Network Manager doesn't suffice.

-Robin

---

