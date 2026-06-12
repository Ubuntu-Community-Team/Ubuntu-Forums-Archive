---
title: "How can Xinerama be completely disabled in Gutsy?"
date: 2007-11-15
forum: Desktop Environments
---

### Post by munckfish on 2007-11-15
Hi

I need to completely deactivate and disable Xinerama in Gutsy because the presence of this extension is disabling Java's Fullscreen Exclusive mode. For background see here: 

[#154613: Java cannot change display modes / screen resolution in Gutsy]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/154613")

In the xorg.conf manpage it indicates that adding the following option in the "ServerFlags" section should disable it, but it's not.

```

Section "ServerFlags"
  Option "Xinerama" "off"
EndSection

```

After restarting X I check in /var/log/Xorg.0.log and find the option is recognised but still when I test Java (and also query the libXinerama API directly with a knocked up C util) it's still present.

Running the same tests on Feisty show Xinerama as not present despite the fact that on both Feisty and Gutsy Xinerama appears to be a built-in module.

Does anyone have any idea how to do this?

Cheers

Dan

---

