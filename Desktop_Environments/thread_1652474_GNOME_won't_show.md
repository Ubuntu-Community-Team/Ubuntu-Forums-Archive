---
title: "GNOME won't show"
date: 2010-12-24
forum: Desktop Environments
---

### Post by BMorganVA on 2010-12-24
I installed Ubuntu 10.04.1 LTS and was able to connect to the internet wirelessly. I ran the update manager and then turned off the computer and turned it back on. Now when I boot into Gnome, all I see is the cursor and the desktop background; although I am able to drag-select and access the right-click menu and the features it provides. The other sessions work fine, including Failsafe Gnome. The problem is I can't connect to the internet in those other sessions. **How can I get the normal Gnome session to work properly?** I have tried reinstalling the OS, and the same problem occurs.

Other problems that occured is that the computer didnot restart itself after installation or after updating, so I forced the computer to shut down and turn back on. Also, before I reach the login screen, I get the following message.

> error: no suitable mode found.
error: unknown command 'terminal'.

I'm not sure if the previously stated problems mean anything or have significance to the major Gnome problem.

Thanks for you help!

---

### Post by WthIteh on 2010-12-25
Reinstalling has no effect on gnome since all configuration will be held in your home directory. You may try to remove .gnome2 folder from your home directory to restore all gnome configurations to their default.

You could also try Alt+F2 which could give you a chance to run a command.
Or Ctrl+Shift+T to open a terminal and do more troubleshooting.

---

### Post by BMorganVA on 2010-12-25
I can't do anything without an Internet connection. When reinstalling my OS to restore the system, what should I do in partitioning to delete all data on the hard drive. Do I Need to mark the partitions for formatting, or not? 

I know this isn't in the right part of the forum' by it's in relation to my major problem.

Thanks again for your help!

---

### Post by Krytarik on 2010-12-26
You should save your personal data (if any) from the partition you are installing to, do it with the LiveCD function of your install disk, and during the install process that partition should be marked for formatting.

---

