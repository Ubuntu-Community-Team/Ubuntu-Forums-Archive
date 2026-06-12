---
title: "Beryl problems"
date: 2007-03-14
forum: Desktop Environments
---

### Post by pappy on 2007-03-14
Hi all
I tried to install Beryl in my machine. Everything worked fine (at least it seemed so). After rebooting the pc there was Beryl configurator installed and something else. I couldn't see beryl so i did a search and i found that i had to run a command to make beryl autostart. I run the command reboot i login Ok but after a while the screen goes black and nothing happens. The Beryl symbol (diamond) appears on the taskbar but nothing else works. The pc freezes. Can someone tell me how to stop Beryl from auto loading at startup? Do i have to login from a command prompt or something.
BTW i installed Beryl through Synaptic. My pc specs are the follow
Kubuntu 6.10 edgy eft
CPu Athlon XP 2800+
1.5 GB RAM
Nvidia Geforce 7600GS 256 MB
Thank you

---

### Post by Waappu on 2007-03-15
Hi

If you have Ubuntu then when you are in login screen press Ctrl+Alt+F1 and then login to virtual terminal
type```
cd ~/.config/autostart
dir
```
You should now see list of autostart programs. Remove beryl and then type```
exit
```and press Ctrl+Alt+F7

---

