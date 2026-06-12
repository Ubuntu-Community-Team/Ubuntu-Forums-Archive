---
title: "Unity gone in 14.04, unable to bring it back"
date: 2016-07-05
forum: Desktop Environments
---

### Post by meetdilip on 2016-07-05
I tried a few of AskUbuntu discussions before deciding it would be wise to ask here. I don't know when I lost Unity desktop. I had to bank on Gnome and Cinnamon I had alongside Unity. I was using one of these alternatives while I noticed that Unity desktop is no longer an option during log in, and is missing. Most guides online say use install ubuntu-desktop. But I am having dependency issues here.

Another thing is I want to upgrade to 16.04. I thought of waiting for the point release, but would go ahead anyway now. But for that, when I use 

```
sudo update-manager -d
```

I get a partial upgrade notice and it fails eventually. When I agree with " Partial Upgrade " option, Ubuntu says " impossible to install ubuntu-desktop " or something similar. The " Partial Upgrade " throws an error and take back to the " Partial Upgrade " option. Thus, I am not able to try 16.04 as well. Please help..

```


$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-desktop : Depends: ubuntu-session but it is not going to be installed
                  Depends: unity-control-center but it is not going to be installed
                  Depends: unity-settings-daemon but it is not going to be installed
                  Recommends: xul-ext-webaccounts but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by TheFu on 2016-07-05
Create a new userid and try to login using Unity from the "gear" selector displayed before login.

Some DEs use the same config files and over time they can cause conflicts.  This is why it is best to always use a different userid when running different DEs on the same computer.

I don't use Unity, so don't know the package to be installed, but you can query **apt** for that.  Something like **apt search unity-** I do see lots of libunity- things on my 16.04 Mate desktop.  If you don't love Unity, don't bother trying to load it. No need.  It is just another program, not the OS.

Best to stick with 1 question per thread.

---

### Post by meetdilip on 2016-07-05
Thanks @TheFu . Actually my installing Unity is related to my desire to upgrade to 16.04. I can manage to live without Unity, but an upgrade to 16.04 requries ubuntu-desktop installed. That's why.

> Create a new userid and try to login using Unity from the "gear" selector displayed before login.

There is no Unity at all in the system now. :(

---

### Post by grahammechanical on 2016-07-05
The Ubuntu developers who design the upgrades from one version of Ubuntu to another base their efforts on a default Ubuntu. They cannot account for all the variations the users make to the OS. So, not only does the upgrade process expect the Ubuntu desktop it does not expect the Gnome shell or the Cinnamon desktops. Do not expect a successful upgrade.

Think about backing up your data and doing a fresh install of 16.04.1 which will be available in a few weeks time.

Regards.

---

### Post by TheFu on 2016-07-05
Might try **aptitude** to see if it can fix the dependency issues. I've found it to be a little smarter than apt-get, synaptic, or whatever GUI tool is included now.

Normally, dependency issues happen, IME, when .deb files are manually installed which have static dependencies (can't be upgraded). This is why staying within the core repos is best, then using a trusted PPA is second best.  If you happen to recall whether any .deb packages were manually installed, removing those could help.

I might try a 14.04 upgrade to 16.04 using a non-Unity system. I'm fairly confident it will work (based on upgrade on that system from 8.xx --> 10.04 --> 12.04 --> 14.04), but haven't tried it. All bets are off.

There's always the manual way to force an upgrade. Just how desperate are you and how good are the backups?  Did you happen to try the upgrade using a DVD/CDROM?

---

### Post by meetdilip on 2016-07-05
Thank you guys. I repeatedly tried 
sudo update-manager -d

and finally I got an upgrade prompt for 16.04. I went with it, and it was successful.Then tried this guide get Unity back

[https://itsfoss.com/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-12-10-quick-tip/](https://itsfoss.com/how-to-fix-no-unity-no-launcher-no-dash-in-ubuntu-12-10-quick-tip/)

---

### Post by meetdilip on 2016-07-05
@grahammechanical

I now have Unity in 16.04. But ctrl+c and ctrl+v not working globally. Ctrl + A is working though. I got nothing on keyboard > shortcut. Can you to tell me how to bring back ctrl c and ctrl v ? Thanks.

---

