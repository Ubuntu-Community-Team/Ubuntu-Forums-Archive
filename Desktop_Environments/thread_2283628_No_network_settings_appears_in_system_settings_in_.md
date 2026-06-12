---
title: "No network settings appears in system settings in Cinnamon - Ubuntu 15.04?"
date: 2015-06-23
forum: Desktop Environments
---

### Post by d-a-johnston-hw on 2015-06-23
I have the cinnamon-desktop-environment meta-package installed on several laptops alongside the standard Unity desktop and Gnome. In all of them network settings doesn't appear in the system settings panel under Cinnamon and clicking on the network applet in the tray to show "network-settings" and clicking on this just gives the full system settings panel (still with no sign of the network settings in it).

Everything is fine and dandy in Unity and Gnome on the same laptops and I couldn't see any obvious bug reports filed against this. Am I missing something obvious in the Cinnamon setup? All the requisite packages appear to be installed.

---

### Post by TheFu on 2015-06-23
Create a new user id and use only one of the DEs with it.  Does that solve the issue?  If so, then it is likely that using the different DEs is causing a conflict.  Pick 1 for each userid.

Otherwise, I haven't a clue.

---

### Post by d-a-johnston-hw on 2015-06-23
> **TheFu said:**
> Create a new user id and use only one of the DEs with it.  Does that solve the issue?  If so, then it is likely that using the different DEs is causing a conflict.  Pick 1 for each userid.

Otherwise, I haven't a clue.


A fresh userid only used with Cinnamon displays the same problem, so if there is some sort of destructive interference with Unity or Gnome it's not at the user level :(

---

### Post by xcorvis on 2015-07-01
I'm also having this problem. I just upgraded from 14.10 to 15.04, I'm just using cinnamon 2.2.16-5ubuntu1 (not cinnamon-desktop-environment and associated packages). It was working before.

> $ cinnamon-settings
/usr/lib/x86_64-linux-gnu/cinnamon-control-center-1/panels/libnetwork.so: undefined symbol: nma_wireless_dialog_nag_user
Failed to load module: /usr/lib/x86_64-linux-gnu/cinnamon-control-center-1/panels/libnetwork.so
Could not find network module; is the cinnamon-control-center package installed?
Could not find bluetooth module; is the cinnamon-control-center package installed?
__init__ took 102.961 ms


The file exists, same perms as the other items in the directory, and those (like sound) work just fine. I tried reinstalling cinnamon-control-center, cinnamon-control-center-data and libcinnamon-control-center1 but no change. Installing cinnamon-bluetooth cleared up the bluetooth module error but the other errors remain. I'm wondering if a change to network manager broke the cinnamon library.

I'm tempted to try one of the Cinnamon 2.4 PPAs.

---

### Post by xcorvis on 2015-07-09
I updated to Cinnamon 2.6 and it has fixed the issue.

---

### Post by Vladlenin5000 on 2015-07-09
Please use the thread tools to mark your thread as solved for the benefit of future forum users. Thank you.

---

