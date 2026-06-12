---
title: "No more Wayland session"
date: 2020-04-04
forum: Desktop Environments
---

### Post by georgesgiralt on 2020-04-04
HEllo,
I recently re-installed my laptop using 19.10 but on a new hard drive and a different partition scheme (full LVM).
I have the wayland packages installed but the GDM session manager only gives the following list :
```
GNOME on Xorg
Gnome Flashback (Compiz)
Gnome Flashback (Metacity)
Ubuntu
Unity
```
the last one I installed because my wife likes it and use it sometimes... 
I've the following packages installed 
```

$ dpkg -l | grep -i wayland
ii  gnome-session-wayland                         3.34.1-1ubuntu2                            all          GNOME Session Manager - GNOME 3 session (transitional package)
ii  kwayland-data                                 4:5.62.0-0ubuntu1                          all          Qt library wrapper for Wayland libraries - data files
ii  kwayland-integration:amd64                    4:5.16.5-0ubuntu1                          amd64        kwayland runtime integration plugins
ii  libkf5waylandclient5:amd64                    4:5.62.0-0ubuntu1                          amd64        Qt library wrapper for Wayland libraries
ii  libqt5waylandclient5:amd64                    5.12.4-1                                   amd64        QtWayland client library
ii  libqt5waylandcompositor5:amd64                5.12.4-1                                   amd64        QtWayland compositor library
ii  libva-wayland2:amd64                          2.5.0-1                                    amd64        Video Acceleration (VA) API for Linux -- Wayland runtime
ii  libwayland-client0:amd64                      1.17.0-1                                   amd64        wayland compositor infrastructure - client library
ii  libwayland-cursor0:amd64                      1.17.0-1                                   amd64        wayland compositor infrastructure - cursor library
ii  libwayland-egl1:amd64                         1.17.0-1                                   amd64        wayland compositor infrastructure - EGL library
ii  libwayland-server0:amd64                      1.17.0-1                                   amd64        wayland compositor infrastructure - server library
ii  qtwayland5:amd64                              5.12.4-1                                   amd64        QtWayland platform plugin
ii  xwayland                                      2:1.20.5+git20191008-0ubuntu1              amd64        Xwayland X server
$
```
And I've tried to reconfigure the gnome-wayland package but to no avail. 
What is wrong ? 
So I'll like all the help i can get and be grateful for that help !

---

### Post by grahammechanical on 2020-04-07
What video hardware do you have? Nvidia? Did you install the Nvidia drivers? You might get what you want if you use the Nouveau drivers instead.

[https://askubuntu.com/questions/1183314/log-in-to-ubuntu-wayland-in-19-10](https://askubuntu.com/questions/1183314/log-in-to-ubuntu-wayland-in-19-10)

Regards

---

### Post by georgesgiralt on 2020-04-07
Hello and thank you for your answer. 
Yes, the computer has a Primus Nvidia card. And yes, I selected to install the Nvidia driver during the installation. 
So I've now reverted to the Nouveau driver and everything seems fine, for now. 
As I previously ran 18.04 LTS on this machine, I thought I could still use Wayland even with the Nvidia driver installed. Apparently, it is no more possible... 
I have to stop taking for granted things that worked fine in one release being good with the new one... But I still wonder why they keep dropping valuable settings/behavior ....
Thank you and stay safe at home !

---

### Post by mc4man on 2020-04-08
If you have the typical optimus laptop then you can undo the nvidia blacklist for wayland.
Then  you'll get a wayland session if nvidia drivers are installed and in use or not.
If in use,  when logging into the wayland session it'll  automatically switch to the Intel gpu for rendering, when logging into any X session the nvidia device will be used for rendering.

Pretty simple, just comment out last line in /lib/udev/rules.d/61-gdm.rules and reboot
Ex.
```
sudo nano /lib/udev/rules.d/61-gdm.rules
```
See screen, added # to front of last line.  (- then  Ctrl+o, Enter, Ctrl+x to write changes in nano if you're unfamiliar..

---

### Post by georgesgiralt on 2020-04-09
Hello,
Apparently, you are right. But this is not the only reason about the lack of the Wayland choice in Gdm menu.
I said so because my problem is on a Dell G3 (3579) with Nvidia Geforce TI-1050 mobile card. On this machine I installed the Nvidia 390 drivers (trough the Ubuntu Installer in 19.10) and after this added other Gnome and Ubuntu shells.
But, on my old laptop (Lenovo THinkpad E540, with same resolution screen and also an Nvidia GK208M [GeForce GT 740M] (rev a1) Primus card and of course a different Intel GPU as well) I also installed 19.10 with the same 390 Nvidia driver and I have Ubuntu on Wayland choice in Gdm. (On this machine I did not install any additional shells )
On the proprietary drivers page, for the graphic card I have 4 choices:
Xorg/Nouveau
Nvidia version 430
Nvidia version 390, selected and installed)
Nvidia version 435 which is said to be tested... 
As I had trouble previously trying to switch Nvidia drivers (resulting in impossibility to run any graphic on those computers), I'm somewhat reluctent to try another one to see if it is still impossible to have Wayland session.
But my point is that the exact chip seems to matter and maybe something else (presence of other sessions shells ? 
Thanks a lot for your help and explanations
Have a nice day and stay safe and indoors !

P.S. : I forgot to say that I used the E540 for years, and that Ubuntu has evolved trough upgrades on it. When I got the Dell, I put the disk from the Lenovo in it and voila. Given the confinement, I decided to make a new install on the Dell using GPT and LVM for anything and upgrade the Windows 7 to Windows 10. This is why I re-installed Ubuntu on the Dell and why I had to install it on an old hard drive on the Lenovo.

---

