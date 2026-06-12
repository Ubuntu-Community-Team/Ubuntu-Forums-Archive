---
title: "can't login/gnome"
date: 2010-04-04
forum: Desktop Environments
---

### Post by renbsr on 2010-04-04
I'm new to ubuntu, I have ubunut 9.04. I downloaded gnome artwork and the instructions said to restart gnome but in my enthousiasm I did not close all programs and I restarted gnome using: **sudo /etc/init.d/gdm restart**. Needless to say my system stopped responding. I rebooted but now I can't login, because the login screen does not appear. When I start my pc, it starts up normally, the ubuntu logo with the progress bar appears but as soon as it reaches about 90%, the logo and progress bar turns mostly green and red. Then there are 3 distorted ubuntu logo's (red and green) which go away and then 2 logo's appear also distorted. After that my systems fails to respond. I have already tried to repair graphical problems using **xfix**, but that doesn't help either. Any suggestions?

---

### Post by Silent Warrior on 2010-04-04
Heh, I don't use recovery mode nearly enough! :) I recognize those distorted logos, though - I recall having them for a while without any indiation of having the problems you're facing, so you can stop worrying about THAT, at least.
Now, throw me a bone here: Does gnome-artwork conflict with any ubuntu-artwork? It sort of sounds like that would be the case, to me. What I'd try to work that out is booting into Recovery, go to a root-terminal with networking and type 'apt-get install ubuntu-artwork'. (If it asks to remove gnome-artwork, I advice you to do just that.) You may also want to run 'dpkg-reconfigure gdm'.

---

### Post by renbsr on 2010-04-04
I tried what you said, this is the result ubuntu artwork is installed and then I tried dpkg reconfiguration. I got the following messages:
* reloading gdm configuration
* changes will take effect when all current x sessions have ended 
invoke-rc.d: initscript gdm, action "reload" failed.

---

### Post by Silent Warrior on 2010-04-07
Hm... Have you got it working yet? I was hoping for someone else to come to the rescue, but it sounds to my untrained ears like a reboot should do the trick from there - looks like a (fairly) normal output. Did it? Otherwise, you could, I suppose, launch gdm manually, if you're dumped to a console. (I think that's [sudo /etc/init.d/gdm start].)

---

### Post by micio on 2010-04-08
could you please post /etc/X11/xorg.conf and /var/log/Xorg.0.log files?

what grafic card you have?
have you loaded some display driver?

many thanks

Micio

---

