---
title: "Terminal won't work on Ubuntu 8.10"
date: 2008-12-13
forum: General Help
---

### Post by Rick429CJ on 2008-12-13
When I open the terminal on Ubuntu 8.10, all I get is a blank window. I can't type anything into it. have tried opening and closing Terminal and opening a new terminal window but always get the same result.

---

### Post by drs305 on 2008-12-13
Have you tried reinstalling it?
```
sudo aptitude reinstall gnome-terminal
```

Have you tried ALT-F2, *gnome-terminal* ? If so, are there any error messages?

---

### Post by albinootje on 2008-12-13
Do you have the same problem with xterm and rxvt ?

---

### Post by fragos on 2008-12-13
I suggest System-> Preferences-> Preferred Applications-> System tab. Normaly it would be "GNOME Terminal" but you'll also be offered xterm and custom as options. Try a diferent terminal emulator to see if that works.

---

### Post by Quid on 2008-12-26
Any joy om this problem? I just had the same thing happen after a reboot (trying to install a new toy usb tablet).

xterm does the same and it's hard to reinstall without the terminal - I need to get out of gnome I guess... 

Also running gnome_terminal from alt f2 does the same.

Any thoughts would be helpful.

---

### Post by Quid on 2008-12-26
Further to my post above - there are a few threads that suggest wrong Nvidia drivers.. I have had this running with the newer Nvidia Xserver Settings Application for months - perhaps some games messed me up ? Regnum WOW are recent installs?

---

### Post by Quid on 2008-12-26
More info for anyone who might help out.. 
My "window bar on th top of my windows is missing ( it think this has been true for weeks and may have no bearing) 

System Monitor acts the same way ( blank) but this too has just started this week.

Compiz and Emerald changes don't seem to help 

Reinstalling Gnome Terminal from Synaptic did not change a thing

 help.... I hope I don't need to do a full install

---

### Post by Quid on 2008-12-30
Solved- for me  - See this link

[http://ubuntuforums.org/showthread.php?p=6459973#post6459973](http://ubuntuforums.org/showthread.php?p=6459973#post6459973)

Quid from Canada:popcorn:

---

