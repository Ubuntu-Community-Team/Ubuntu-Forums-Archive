---
title: "X doesn't work until being killed on boot"
date: 2013-04-27
forum: Desktop Environments
---

### Post by ksteuber on 2013-04-27
I have spent much of the day today trying to get a graphics card to work with an Ubuntu computer. It is a Radeon HD 5830. As far as I can tell, the available drivers are fglrx and radeon. I tried both and couldn't get either to work easily. Finally I totally removed fglrx (apparently not totally - /var/log/Xorg.0.log says it tries to load fglrx but it does not exist. I don't know why it is still trying to do this, but I THINK it is not causing any problems so I am just leaving it alone). Now, when the server starts, there seems to be no interface. It doesn't go to the command line login screen either like it would with no graphical interface installed. It just sits at the screen with the startup messages and does nothing. If I switch to tty1 or ssh in and kill -9 the Xorg process, the process restarts itself and X starts working properly. I am utterly baffled; I googled around and was unable to find anything like this. 

Does anyone have any ideas as to how to troubleshoot/fix this? It seems like my configuration is working, just not right when the computer starts. Also, I don't know if this is at all related, but X seems to run on display :1 instead of :0.

---

