---
title: "thunar stuck maximized"
date: 2013-05-31
forum: Desktop Environments
---

### Post by willcoq on 2013-05-31
I installed Xubuntu earlier this week. Yesterday, I decided to check "Save session for future logins" before logging out just to try it out. When I logged back in, all of my windows were maximized. I was able to get everything back to normal except the file manager, thunar. It is stuck maximized, and it the minus, plus, and close window buttons are unresponsive.

How do I reset thunar preferences? I already tried mv ~/.config/Thunar ~/.config/Thunar.bak

I have also tried setting a custom resolution for windows in Window Rules in Compiz. No luck. Also tried deleting all saved sessions and rebooting.

Secondary question - In my top panel, there is a black exclamation point inside a red alert symbol. It says I have updates. I can click it to show or install the updates, and if I click it, the Software Updater opens and says I have security updates for Xubuntu base. However, when I type in terminal "sudo apt-get update" followed by "sudo apt-get upgrade" there are no upgrades.

Is there a way to install these updates via terminal instead of through the panel button?

---

### Post by dentaku65 on 2013-06-01
Try
```
sudo rm -r $HOME/.cache/sessions
```
Reboot

---

### Post by binaryhermit on 2013-06-02
It's also possible you've put it in fullscreen mode, try pressing F11
EDIT: And it's ```
sudo apt-get dist-upgrade
``` not ```
sudo apt-get upgrade
```

---

