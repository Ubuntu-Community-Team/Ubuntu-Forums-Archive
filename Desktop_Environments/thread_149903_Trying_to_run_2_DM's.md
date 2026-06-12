---
title: "Trying to run 2 DM's"
date: 2006-03-24
forum: Desktop Environments
---

### Post by chugru on 2006-03-24
Hi, all...

Here's my objective... I have kubuntu installed and working well. I also want to give XFCE a trial run and maintain the ability to start and run KDE whenever I wish.

The first thing I did was remove KDE from initial startup:```
sudo update-rc.d -f kdm remove
```...Then, I installed xubuntu with xfce4:```
sudo apt-get install xubuntu-desktop
```...Now, when I boot the system, I get a login prompt, and **startx** starts up XFCE.

My question... What command would I use to start KDE from command prompt??

I want 2 commands when I boot to command prompt, one which will start XFCE the other which will start KDE.

Does anyone have a suggestion as to how I can pull this off??

Thanks!! :D

---

### Post by WolfJay_83 on 2006-03-24
You don't want to use a display manager?  Once you install Xfce (or Gnome or any other WM for that matter), KDM will give you the option to select which desktop to start at the login screen. 

If you are running multiple desktop wm's, then your best bet is to use a display manager (KDM, GDM, or XDM).  Starting from command prompt requires configuring your ~/.xinitrc file.

---

### Post by chugru on 2006-03-24
**WolfJay_83 wrote:**> You don't want to use a display manager? Once you install Xfce (or Gnome or any other WM for that matter), KDM will give you the option to select which desktop to start at the login screen.

I'm ok with a display manager and have kdm on my system. I don't know how to make it give me the option of which desktop to start. Do you have any suggestions as to how I must set it up?

Also, since I ran: ```
sudo update-rc.d -f kdm remove
```...How do I restore it to functionality??

Thanks...

---

### Post by WolfJay_83 on 2006-03-27
The easiest way would be to reinstall kdm.  The easiest way to do that would be to open synaptic.  (you can open it by typing "sudo synaptic" into a terminal).
Do a search for kdm, right click on it and select reinstall.  Click the apply button to reinstall.

When you reboot the computer, it should open the kdm login manager.  There should be three buttons below login, the first being "session type", if you click that it should give you the option of xfce or kde.

note: if this doesnt immediatly work, the easiest thing may to reinstall xubuntu-desktop and kubuntu-desktop from synaptic in a simmilar way.  That will make sure everything is configured properly (but you wo'nt loose settings)

---

### Post by chugru on 2006-03-27
[QUOTE=WolfJay_83]The easiest way would be to reinstall kdm.  The easiest way to do that would be to open synaptic.  (you can open it by typing "sudo synaptic" into a terminal).
Do a search for kdm, right click on it and select reinstall.  Click the apply button to reinstall.

When you reboot the computer, it should open the kdm login manager.  There should be three buttons below login, the first being "session type", if you click that it should give you the option of xfce or kde.

note: if this doesnt immediatly work, the easiest thing may to reinstall xubuntu-desktop and kubuntu-desktop from synaptic in a simmilar way.  That will make sure everything is configured properly (but you wo'nt loose settings)[/QUOTE]
Great suggestion. Now I have things working fine!

Thanks a lot!

---

