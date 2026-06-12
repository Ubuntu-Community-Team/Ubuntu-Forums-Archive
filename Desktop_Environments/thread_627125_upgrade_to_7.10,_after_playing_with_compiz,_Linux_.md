---
title: "upgrade to 7.10, after playing with compiz, Linux GUI no more"
date: 2007-11-29
forum: Desktop Environments
---

### Post by drewcoon on 2007-11-29
I just updated to Gutsy, and tried using Compiz but it didn't work (gave me a composite extension not found message). I followed someone else's instructions in a post who was helping someone else with the same problem I had by installing something (I can't remember what it was, since without a GUI i'm having some trouble getting to my Linux browser history). Compiz worked afterwards, but very laggy. I then turned the effects off, but the lag continued (very bad lag, worse than my ATI card without 3D acceleration). I disabled the restricted driver for my ATI card and restarted, because that's fixed my problems in the past, only to get this ominous message:

Failed to start X Server
Failed to load module "fglrx" (Module does not exist, 0)

Fatal server error
no screens found

It then started up in command prompt.

I tweaked the xserver around (dpkg-reconfigure xserver-xorg) and I now have the GUI for the login screen, but after I log in I'm faced with a white screen.

I'm posting this from Windows... Help please! :(

---

### Post by drewcoon on 2007-11-29
UPDATE --- I reinstalled the driver through terminal, but the entire system is still ridiculously laggy... Any help? :)

---

### Post by drewcoon on 2007-11-29
Alright, I just fixed it... The lag was caused by using xserver-xgl, which I just took out and now the system response is as crisp as it was before the update :)

---

