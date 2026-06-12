---
title: "Cannot see volume indicator in task bar. [Ubuntu 14.04]"
date: 2014-06-15
forum: Desktop Environments
---

### Post by jkdublin00 on 2014-06-15
Hello everyone. When I first turn on my computer, in the user login screen i can see and use the volume/sound indicator at the top of the screen. However, after i login to my user the sound indicator disappears. I installed the indicator-applet-complete package with no issues. Can someone tell me how to make the sound indicator appear again? Thanks.

---

### Post by grahammechanical on 2014-06-15
The sound app indicator is usually installed by default and the setting is set to the mid point so that the screen reader will work without someone needing to unmute sound.

System Settings>Sound and tick "show sound volume in the menu bar."

Regards.

---

### Post by zhongfu2 on 2014-06-17
> **grahammechanical said:**
> The sound app indicator is usually installed by default and the setting is set to the mid point so that the screen reader will work without someone needing to unmute sound.

System Settings>Sound and tick "show sound volume in the menu bar."

Regards.
Ah, thanks a lot! I've been scratching my brains out, reinstalling this and that but stupidly I glaringly missed the obvious option in the sound menu.

---

### Post by badjonathanmaster on 2015-04-05
For those who have the "show sound volume in the menu bar." marked, and still have the same problem, just try this: 


[LIST]
[*]Open terminal and execute these commands:
  sudo dpkg-reconfigure $(dpkg -l | grep indicator-sound | awk '{print $2}' | tr '\n' ' ')
sudo update-initramfs -u

[*]Logout/restart your system and check whether you get the sound indicator
[/LIST]
  If above doesn't help then try to re-install indicator-sound by executing this command:
  sudo apt-get -f install --reinstall indicator-sound indicator-sound-gtk2
  Again logout/restart your system.
  Reply if you get any error at any particular command with the error message.

---

