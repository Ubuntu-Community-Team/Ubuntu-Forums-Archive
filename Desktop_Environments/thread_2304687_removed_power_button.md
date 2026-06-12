---
title: "removed power button"
date: 2015-11-29
forum: Desktop Environments
---

### Post by Hankbonk on 2015-11-29
I have Lubuntu 14.04 LTS .  I have removed the power/reboot/shutdown button on the right lower part of my screen by accident  How can I restore it ?

---

### Post by ajgreeny on 2015-11-29
Copy the **/usr/share/applications/lubuntu-logout.desktop** file to your **/home/*username*/.local/share/applications** folder, then make it executable and it should show as an option to add to an application-launchbar, which you can add at the end of the panel with a right click.

This is all from memory, so some of the details may be incorrect, but I think it is largely right; you may just need to search a bit harder for the files as the names may be different from what I remember.

---

### Post by Rex Bouwense on 2015-11-29
From the Community Help wiki,  [https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#Shutdown_Button_is_missing_from_LXPanel.2C_how_can_I_add_it.3F](https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#Shutdown_Button_is_missing_from_LXPanel.2C_how_can_I_add_it.3F)

---

### Post by Hankbonk on 2015-12-10
Thanks ajgreeny and Rex Bouwense, it worked out !

---

