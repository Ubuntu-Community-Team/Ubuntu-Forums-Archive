---
title: "Another video disaster KDE won't start"
date: 2011-07-13
forum: Desktop Environments
---

### Post by gizmobay on 2011-07-13
I'm running 11.04 amd64 with nouveua drivers using a Gefore 7300LE card. I did an update and then it wouldn't boot at all. I ended up adding nomodeset and now it will boot. I can log into gnome classic no effects but when I try KDE I get a black screen with a mouse. I disabled composite in the kwinrc file and I went as far as to remove all of compiz but no matter what I do I can't get it to start.

I see in the kdm.log file it says no nvidia module. I'm not using nvidia and I don't have an xorg.conf file. Nothing of nvidia is installed. I also see it says Not connected to dbus server. Check if the dbus is started. Any suggestions?

---

### Post by jtarin on 2011-07-13
Before logging in, switch over to another terminal (Ctrl + Alt + F1-F6) and login. Then run the command ```
startx
``` If it complains use ```
sudo startx
```.Report back.

---

### Post by gizmobay on 2011-07-13
I did an update this morning and now all is working, thanks.

---

