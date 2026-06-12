---
title: "&quot;Add remove programs&quot; vanished from applications menu!"
date: 2005-11-25
forum: Desktop Environments
---

### Post by anil_robo on 2005-11-25
**Problem:**

I was trying out several new third-party packages, but didn't like any of them in Ubuntu 5.10, so I uninstalled them using their own removal scripts. But soon I discovered that the "add remove programs" entry had vanished from the applications menu! But the Synaptic package manager is present in the System->Administration menu. Smeg shows that there is no entry named "add remove programs" anymore!

What should I do to get back the add remove programs entry on my applications menu?

** Solution:**

I downloaded "Easy Ubuntu" and tried to install a few apps with this tool. It didn't work. So I uninstalled Easy Ubuntu, and my "Add Applications" button was gone with it.
 
 I thought EasyUbuntu deleted the program icon only. But I found out that it had uninstalled the entire "Add Applications" program. I booted in Live CD to see what is the command for "Add Applications" (type smeg in terminal, then double click on "Add Applications" icon to see details). It was gnome-app-install. Then I booted from HD and carried out a search for "gnome-app-install". It was not found. So I reinstalled it from the repositories, guessing that it should be "sudo apt-get install gnome-app-install" and bingo! Ubuntu reinstalled "Add Applications" and everything is working fine now.
 
 Let's not only post our problems in forums, but also any solutions we may find/know! The joy is in sharing! :grin:

---

### Post by linbetwin on 2005-11-25
This only happened to me when I upgraded to Dapper.

---

### Post by anil_robo on 2005-11-25
I'm not comfortable if I don't see that add remove program over there. It effectively prevents me from installing new programs the easy way because I'm not very comfortable with commandline or the synaptic details. Someone please help how can I get back the "add remove programs" back on the Applications menu?

---

### Post by anil_robo on 2005-11-26
I downloaded "Easy Ubuntu" and tried to install a few apps with this tool. It didn't work. So I uninstalled Easy Ubuntu, and my "Add Applications" button was gone with it.

I thought EasyUbuntu deleted the program icon only. But I found out that it had uninstalled the entire "Add Applications" program. I booted in Live CD to see what is the command for "Add Applications" (type smeg in terminal, then double click on "Add Applications" icon to see details). It was gnome-app-install. Then I booted from HD and carried out a search for "gnome-app-install". It was not found. So I reinstalled it from the repositories, guessing that it should be "sudo apt-get install gnome-app-install" and bingo! Ubuntu reinstalled "Add Applications" and everything is working fine now.

Let's not only post our problems in forums, but also any solutions we may find/know! The joy is in sharing! :D

---

