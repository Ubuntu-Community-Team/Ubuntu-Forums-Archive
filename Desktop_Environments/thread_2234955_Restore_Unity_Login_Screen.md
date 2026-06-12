---
title: "Restore Unity Login Screen"
date: 2014-07-17
forum: Desktop Environments
---

### Post by Louisda16th on 2014-07-17
I installed xfce using 'sudo apt-get install xubuntu-desktop' to try it out. My log in screen has changed and I want it back. Removing all xfce packages didn't help. Reinstalling / purging and installing ubuntu-desktop didn't work either. Some threads say I should run 'sudo dpkg-reconfigure lightdm'. Lightdm is already my window manager and running that command doesn't help as well. Could someone please help me get my original Ubuntu desktop back. Thanks in advance! :)

EDIT:

Solution to my problem was to purge lightdm-gtk-greeter i.e. I had to run

```

sudo apt-get purge lightdm-gtk-greeter

```

I guess the trick is to have just unity-greeter and none of the others installed.

---

### Post by Dennis N on 2014-07-18
To get the unity-greeter back the first of the answers here might help:

[http://askubuntu.com/questions/75755/how-to-change-the-lightdm-theme-greeter](http://askubuntu.com/questions/75755/how-to-change-the-lightdm-theme-greeter)

Restart may be needed.

---

### Post by Louisda16th on 2014-07-18
Thank you for your reply. I've checked that link as well and my /etc/lightdm/ didn't have a lightdm.conf (the directory had 3 files). I'm using Ubuntu 14.04 64-bit.

After some experimentation, it seems that all I had to do is uninstall lightdm-gtk-greeter.

---

