---
title: "White Screen of Death on Jaunty"
date: 2009-05-03
forum: Desktop Environments
---

### Post by ionFreeman on 2009-05-03
So... I started getting WSODs when logging in after changing some mount options for an external drive -- I don't know if that was related. I also turned on some Compiz features. I could kill the x-session-manager and try again until I got a desktop. I installed (along apparently, with all of KDE) and ran EnvyNG. It claimed to be installing a number of drivers, and rebooted.

Now, I can't get a desktop at all. However, my wife's login is just fine (which is how I'm running a browser.) If I kill just dbus-launch, I can see my desktop background, so I'm pretty sure this is a Compiz problem. Running Compiz-Check gives me a big thumbs up.

I'd like to just copy her compiz configuration over mine, or set mine back to the default. How do I do that?

---

### Post by ionFreeman on 2009-05-03
I marked Compiz for complete uninstallation and applied in Synaptic. I could then log in, and reinstall it. And I could log out, and log in. I think my desktop's working again.

---

