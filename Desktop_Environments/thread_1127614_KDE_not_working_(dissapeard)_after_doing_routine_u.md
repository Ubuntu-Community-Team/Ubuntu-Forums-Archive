---
title: "KDE not working (dissapeard) after doing routine update"
date: 2009-04-16
forum: Desktop Environments
---

### Post by Garpur on 2009-04-16
Hi all

I have a "little" problem related to getting KDE to work again on Ubuntu. 

**The whole thing started with me doing my routine update of (k)ubuntu system.** 
After I rebooted my system I suddenly got the Gnome login manager instead of my usual KDE login manager. When I then go to the session manager and choose option “3. kde desktop” and log on I get the following message:

> Xsession unable to launch “/usr/bin/startkde” X session ---”/usr/bin/startkde” not found. Falling back to default session.

[B]
OK, I from this assume that KDE has somehow been remove in the upgrade process.[/B] 
My next step is then to re-install “*kubuntu-desktop*” in Synaptic Package Manager. It gets stop by the message:

> 
Could not mark all packages for installation or upgrade
The  following packages have unresolved dependancies . Make sure that all required repositeries are added and enabled in the preferences. 

Then comes a long list of what kubuntu-desktop depends on but it is not going to install those softwares.  ](*,)

I have also tried installing in terminal with same results:
> 
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: 
Depends: ark but it is not going to be installed
                   Depends: dolphin but it is not going to be installed
                   Depends: dragonplayer but it is not going to be installed
                   Depends: kde-window-manager but it is not going to be installed
etc...........................

Any good ideas for how to solve this are very much appriciated!

Best regards
Garpur

---

