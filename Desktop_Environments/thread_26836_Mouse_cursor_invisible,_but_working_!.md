---
title: "Mouse cursor invisible, but working !?"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Claudiu on 2005-04-14
Hi there!

I'm (almost) beginner in Linux and after have tryed several distros I've choosed to stick with Ubuntu. 

After a while (upgrading, installing some packages, Kubuntu Desktop, themes, etc.) my mouse cursor didn't show on the screen, but the mouse itself works (it means I can move the cursor which is invisible and click on links and buttons). I don't know exactly what I did to cause this problem. Maybe 'sudo apt-get dist-upgrade' (which ended with an error at last package - kdelibs - but this is another problem). I have installed Ubuntu on another machine and have copied the "mouse" section from /etc/X11/xorg.conf to my first system. The mouse cursor is still invisible but working. Also I have changed mouse cursors (after moving the mouse like a blind man) in Control Center. Restarted. Still invisible.

Please give me some ideas about what can I do to make my mouse work.

Thank you.

---

### Post by erkki70 on 2005-04-14
Hi,
So far the best would be to post here your xorg.conf file and your specs so people could help better. ;-)
However you could try to reconfigure your X server:
```
sudo dpkg-reconfigure xserver-xorg
``` and maybe set your pointer to use psaux  instead of dev/input/mice to see if it's help...

Cheers,
Erkki

---

### Post by Claudiu on 2005-04-15
I've made a reinstall.. and all it's ok now :)

I think it was the kde theme... I don't know.

---

