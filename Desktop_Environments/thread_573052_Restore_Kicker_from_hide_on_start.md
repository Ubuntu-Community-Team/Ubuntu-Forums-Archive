---
title: "Restore Kicker from hide on start?"
date: 2007-10-11
forum: Desktop Environments
---

### Post by schreckles on 2007-10-11
Ok, so I just got rid of GNOME for the KDE, and already broke something. My friend was gonna "show me something cool", and now my kicker is gone. I can bring it up using the command, but I want it to start with kubuntu, like it's supposed to.

If it helps at all, this is the code he put in in the konsole to try and "show me something cool"...

" kwriteconfig --file ~/.kde/share/autostart/panel.desktop --group "Desktop Entry" --key Hidden true "

I tried just changing it so that it was the same, but rather than having it say true at the end, making it say false to TRY and get it to show back up, but it didn't work. Any help would be appreciated.

---

### Post by linuxwizard on 2007-10-11
Bring up your kicker > right click on it > choose configure panel > a window will come up look through there > There should be  2 or 3 choices how the kicker will act. You want to take it off auto hide.

---

### Post by schreckles on 2007-10-11
Thank you, but it isn't on "auto-hide" at all. I checked that already to make sure. The only time it's hidden is on the startup, and I think I'm gonna need to run something via the konsole to get it back to normal, but I'm not sure what. Any other help is greatly appreciated. Thanks a ton for your input though.

---

