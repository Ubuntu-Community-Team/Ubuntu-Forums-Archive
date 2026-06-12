---
title: "kdm dying at boot - no graphical login"
date: 2011-11-23
forum: Desktop Environments
---

### Post by Guy_H on 2011-11-23
I tried posting this in General Help, but I think this is probably the proper place for it.


Strange problem, system boots normally, I get the splash screen with the 'dots' but then nothing.

I can Ctrl-F1 to a terminal, login and then run startx& and the KDE desktop runs fine (although Muon doesn't authorise now and there are another couple of issues)

Looking in syslog, the only things that do not look right are

```
Nov 19 10:57:58 AMARI-UBUNTU kernel: [   17.878884] init: apport post-stop process (951) terminated with status 1
Nov 19 10:57:58 AMARI-UBUNTU kernel: [   17.923107] init: kdm main process (912) killed by TERM signal
Nov 19 10:57:58 AMARI-UBUNTU kernel: [   17.938369] init: gdm main process (950) killed by TERM signal

```

kdm.log is empty
nothing weird in Xorg.0.log


I don't know enough about the boot process to delve much deeper :(

Any ideas or pointers please .....

---

### Post by poomerang on 2011-11-25
same problem here. especially, it appeared after removing gdm, but I don't know if it's related or if it's instead some upgraded package that introduced the issue.

---

### Post by gordintoronto on 2011-11-25
Did you initially install Kubuntu, or did you add KDE later? What version?

---

### Post by poomerang on 2011-11-28
problem solved for me.

it appears that removing gdm while it was selected to be the default DM was actually the problem.

by installing gdm again, and then switching between kdm and gdm as default (so that all configuration files were correctly cleaned up) solved the issue for me.

in short:
sudo apt-get install gdm (and when conf dialog appears, select the DM that is not currently set)
sudo dpkg-reconfigure gdm (and select again the default wished DM)
sudo apt-get remove gdm

still I believe there might be a bug, as uninstalling one DM (though the default one) should not lead to a non-graphical-boot but to selecting the other one as default, shouldn't it?

BTW, I also tried to just dpkg-reconfigure kdm when gdm was uninstalled, but that didn't make any difference
and also update-rc.d kdm defaults didn't work (apparently kdm wasn't even loaded at startup at first!)

@gordintoronto: oneiric version, kubuntu installed first, then gnome added and removed short after

---

### Post by Guy_H on 2012-02-04
> **poomerang said:**
> problem solved for me.

it appears that removing gdm while it was selected to be the default DM was actually the problem.

by installing gdm again, and then switching between kdm and gdm as default (so that all configuration files were correctly cleaned up) solved the issue for me.

in short:
sudo apt-get install gdm (and when conf dialog appears, select the DM that is not currently set)
sudo dpkg-reconfigure gdm (and select again the default wished DM)
sudo apt-get remove gdm

still I believe there might be a bug, as uninstalling one DM (though the default one) should not lead to a non-graphical-boot but to selecting the other one as default, shouldn't it?

BTW, I also tried to just dpkg-reconfigure kdm when gdm was uninstalled, but that didn't make any difference
and also update-rc.d kdm defaults didn't work (apparently kdm wasn't even loaded at startup at first!)

@gordintoronto: oneiric version, kubuntu installed first, then gnome added and removed short after

:D

Thank you - for some reason I did not get a notification of any replies !!

After a recent update even my 'login and startx' workaround stopped functioning properly so today I started looking at this again and you are spot on.

I can repeat the issue as well.
Kubuntu install, then install gdm, set as default, remove gdm, trashes config which cannot be reconfigured without reinstalling gdm and using 'sudo dpkg-reconfigure gdm' to select kdm first


Thank you :D

---

