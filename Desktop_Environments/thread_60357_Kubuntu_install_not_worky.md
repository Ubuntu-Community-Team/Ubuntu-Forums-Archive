---
title: "Kubuntu install not worky"
date: 2005-08-27
forum: Desktop Environments
---

### Post by Dustin Wyatt on 2005-08-27
I installed kubuntu via apt-get install kubuntu-desktop.

I selected KDM as my display manager.

When I try to login to a KDE session I get these errors:

```

There was an error setting up inter-process communications for KDE.  The message returned by the system was:

Could not read network connection list.
/home/thermo/.DCOPserver_ubuntu__0

Please check that the "dcopserver" program is running!
```

When I press OK on that dialog box the same message pops back up and I press OK on that and then another dialog pops up over that one saying:

```

Will not save configuration.

Configuration file "/home/thermo/.kde/share/config/ksmserverrc" not writable.

Configuration file "/home/thermo/.kde/share/config/kdeglobals" not writable.

Please contatct your system administorator.

```

When I click OK on that dialog my screen goes blank and then it goes back to the regular kubuntu login screen.  I can only log into Gnome.  :(

---

### Post by Dustin Wyatt on 2005-08-27
Ok, for anyone having the same issues change the ownership of the .kde directory in your home directory to yourself.

For some reason I didnt own the directory...

---

