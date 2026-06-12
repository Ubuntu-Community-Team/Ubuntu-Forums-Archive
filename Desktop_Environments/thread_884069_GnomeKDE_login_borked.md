---
title: "Gnome/KDE login borked"
date: 2008-08-08
forum: Desktop Environments
---

### Post by BoredOutOfMyMind on 2008-08-08
Night before last I installed K3B to burn a couple of CD's. 

No issues, and when it wanted to install KDE4-KDM, I was not alarmed.   

Yesterday Firefox froze and so I did Alt-Ctrl-Backspace and nothing . Black screen.    Now I cannot get in at all with reboot and it is hanging on a KDM login. Apt-get remove/install KDE4-KDM and GDM did not work. 

I get to the root and can login but startx will not let me in. :(

Any suggestions to fully remove kdm from command line? :confused:

---

### Post by BoredOutOfMyMind on 2008-08-08
This is 8.04

---

### Post by annda on 2008-08-08
in similar cases i always removed .Xauthority and it helped. but i'm just a dilettant, so PLEASE BACK UP the file before trying out the suggestion.

---

### Post by benerivo on 2008-08-08
To fully remove kdm from the command line use```
sudo apt-get purge kdm-kde4
```Then you want to make sure that gdm is set as your default login/display manager. I think you should be able to do this with```
sudo nano /etc/X11/default-display-manager
```and make sure the first and only line reads```
/usr/bin/gdm
```(Another way to set a default is when you install any display manager, it will bring up a dialog asking you to pick which one.)

Then type```
sudo /etc/init.d/gdm start
```This should start gdm.

---

### Post by BoredOutOfMyMind on 2008-08-08
> **benerivo said:**
> To fully remove kdm from the command line use```
sudo apt-get purge kdm-kde4
```Then you want to make sure that gdm is set as your default login/display manager. I think you should be able to do this with```
sudo nano /etc/X11/default-display-manager
```and make sure the first and only line reads```
/usr/bin/gdm
```(Another way to set a default is when you install any display manager, it will bring up a dialog asking you to pick which one.)

Then type```
sudo /etc/init.d/gdm start
```This should start gdm.

I will try the purge tonight. 

Thank you for the reply.

---

### Post by BoredOutOfMyMind on 2008-08-08
:confused::confused:I have reinstalled gnome-core and gdm to no avail.

At reboot, it seeks a kde4 file, so I installed kde4-core.

nothing will pull up gui.....

---

### Post by benerivo on 2008-08-09
What kde4 file does it mention?

Try installing wdm from the command line. It will then ask you which login/display manager you want to use for default (choose wdm). Then reboot. It should then load up with the wdm login screen. From here you can select to start the gnome desktop. I would guess that ubuntu shouldn't require any kde4 files to be loaded before it brings up this login screen.

A long shot is that it might be a problem with your display settings, which you could try reconfiguring with```
sudo dpkg &#8211;reconfigure &#8211;phigh xserver-xorg
```and answering some questions about your graphics card, monitor, keyboard, etc.. Just go with the default option if you are unsure of the answers.

---

