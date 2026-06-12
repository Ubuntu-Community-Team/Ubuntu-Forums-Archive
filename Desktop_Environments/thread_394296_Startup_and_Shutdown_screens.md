---
title: "Startup and Shutdown screens"
date: 2007-03-26
forum: Desktop Environments
---

### Post by swordfury on 2007-03-26
I'm running Ubuntu 6.10 Edgy Elf with Gnome.  I wanted to checkout KDE and I have installed it and selected it.  I now do not want to run KDE anymore and have select Gnome as my default session.  But when Ubuntu starts up and shuts down I see the blue Kbuntu logo's.

Does anyone know how I can restore these startup/shutdown screen back to the default "brown" Ubuntu screens?

Thanks

---

### Post by will_in_wi on 2007-03-26
How did you install KDE? If you installed kubuntu-desktop then to remove KDE you need to uninstall kubuntu-desktop. After uninstalling kubuntu-desktop you need to open a terminal and type:
```
sudo apt-get autoremove
```
Look through the list and make sure that there are no programs you use in there. If there are then write them down and reinstall them after you are done.

After you have completed this, reboot and the system should be back to normal.

---

### Post by swordfury on 2007-03-26
Thanks for the reply.  I went here
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

and followed the steps to install KDE.  I ran this **sudo aptitude remove kubuntu-desktop** to uninstall KDE which removed everything execpt the boot up screen.  Now when I boot ubuntu I only have the Kbuntu start up screen but everything else is normal.

Thanks.

---

### Post by will_in_wi on 2007-03-26
Open synaptic and see if kubuntu-artwork-usplash is installed. If it is uninstall it. Then reinstall usplash-theme-ubuntu.

---

### Post by swordfury on 2007-03-26
That did it, thank you very much.  One last question.  Is it customary for Keyring to ask me for my password everytime I reboot to connect to my wpa wireless network?

Thanks and goodnight.

---

### Post by will_in_wi on 2007-03-26
Yes, keyring will do that. There are possible workarounds for this.

[http://www.ubuntuforums.org/showthread.php?t=349984&highlight=gnome+keyring+pam](http://www.ubuntuforums.org/showthread.php?t=349984&highlight=gnome+keyring+pam)

---

