---
title: "GNOME won't start fully"
date: 2008-02-13
forum: Desktop Environments
---

### Post by eku on 2008-02-13
I have this problem with GNOME. After typing username and password to the login screen, the screen disapperas, and mouse in the middle of the orange/brown screen appears. Just that. Nothing else.

This started when I tried switching default resolution in Xorg.conf (switched order of "1280x1024" and "1024x768" in modes section). After the change, I restarted gdm. That was the only thing I did to Xorg.conf.

I tried to switch it back. Didn't work. I even tried to "reset" xorg.conf by running the dpkg-reconfigure xserver...whatever it was.

My computer has build-in Intel graphics gard. I switched "intel" to "vesa" in xorg.conf, didn't help.

Which logs should I search for possible clues? Is there a way to fix this?

I'm running Ubuntu 7.10.


edit: I think I solved this. Just removed gdm, reboot, install ubuntu-desktop.

L

---

### Post by ola on 2008-02-13
I'm not sure but you can try to change name of your X11 config file (something like sudo mv /etc/X11/xorg.com /etc/X11/xorg.conf.bak and hope you get X upp and running with failsafe X.

If that doesn't help try to copy the log file (/var/log/xorg.log (not really sure about the name of the log file so just look around)) and attach here and hopefully someone will be able to help out.

If you look in the log file yourself try to find lines starting with EE and WW which stands for errors and warnings. Eventually you will be able to figure something out yourself.

---

### Post by eku on 2008-02-20
Okay, now I tried some more hackin' and crackin', and now all I get is remote login. Nothing else.

I've edited gdm.conf, xorg.conf, reverted both back, tried "reseting" x trhough sudo dpkg-reconfigure xserver-common (or something like that), rebooting...

Nothing seems to work.

Is there a way to complitely remove X and everything related to it? I want to fully "reset" this whole thing now, but I don't want to re-install whole system again...

L

---

