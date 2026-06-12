---
title: "Disabling the touchpad tap"
date: 2005-08-19
forum: Desktop Environments
---

### Post by natpond on 2005-08-19
i have searched all over the internet for a way to disable the touchpad tap function on my Sony VAIO V505 laptop. it is ENRAGING to click somewhere else by accident when i am typing, so this really needs to happen. I am COMPLETELY new to linux/Ubuntu, so a complete step by step is preferred if not necessary to help me.

Thank you all so much for any help you can provide,
Nat

---

### Post by art on 2005-08-20
I am not sure if it uses synaptics driver for touchpad, but I think it does. In that case go to System->Administration->Synaptic Package Manager. Search for qsynaptics. Install it. Then open qsynaptics, and in the tab "Tapping" uncheck "Use Tapping"
HTH

---

### Post by rhystic on 2005-08-20
you could also put:

        Option        "MaxTapTime"              "0"

in /etc/X11/xorg.conf  in  the synaptics section to disable the touchpad click

---

### Post by natpond on 2005-08-21
[QUOTE=art]I am not sure if it uses synaptics driver for touchpad, but I think it does. In that case go to System->Administration->Synaptic Package Manager. Search for qsynaptics. Install it. Then open qsynaptics, and in the tab "Tapping" uncheck "Use Tapping"
HTH[/QUOTE]
 i tried to install the qsynaptics driver thing off of synaptic, but it says it needs to uninstall ubuntu-desktop and xorg-driver-synaptics, which was unsettlign because i dont knwo what those are, but i obliged and clicked okay, but an error comes up that says that the following packages have unresolvable dependencies etc etc, then says this:
qsynaptics:
 Depends: xfree86-driver-synaptics but it is not going to be installed

so what do i do?

and also, i tried the other technique mentioned, but it seems to do nothing... wierd.

thanks,
Nat

---

### Post by aveline on 2005-08-21
[QUOTE=natpond]i tried to install the qsynaptics driver thing off of synaptic, but it says it needs to uninstall ubuntu-desktop and xorg-driver-synaptics, which was unsettlign because i dont knwo what those are, but i obliged and clicked okay, but an error comes up that says that the following packages have unresolvable dependencies etc etc, then says this:
qsynaptics:
 Depends: xfree86-driver-synaptics but it is not going to be installed

so what do i do?

and also, i tried the other technique mentioned, but it seems to do nothing... wierd.

thanks,
Nat[/QUOTE]
 the other method requires you to restart Xwindow by logging out back to the login screen or hitting ctrl alt backspace then logging in again.

aveline

---

### Post by art on 2005-08-21
Yeah, now that you said I remember getting the same errors. I think I downloaded it from their sourceforge site, and installed from source. Go to 

[http://qsynaptics.sourceforge.net/dl.html](http://qsynaptics.sourceforge.net/dl.html)

and download the QSynaptics 0.2: "circular argument". And then install it (Just in case you don't know how to install from source. In command line go to directory you downloaded the file to. Type tar -jxf qsynaptics-0.2.tar.bz2. Now go to qsynaptics-0.2 and type qmake and then make. This should be it. Sorry if I am saying obvious...). Should work. 
HTH

---

