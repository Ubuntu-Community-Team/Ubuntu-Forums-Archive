---
title: "problem with Xorg on Kubuntu 18.04"
date: 2018-05-06
forum: Desktop Environments
---

### Post by alain.roger on 2018-05-06
Hi,

sometimes my PC starts and does not display the DE. I can go to terminal with CTRL+ALT+F2 e.g. and type "startx". In thiscase i got information that i have to check /home/alain/[FONT=monospace][COLOR=#000000].local/share/xorg/Xorg.1.log as DE does not start.


[/COLOR]When i check this log i have no error (EE) regarding the Xorg or graphic card. If i reset the PC pressing the reset button on my computer, the DE starts normally most of the time.
So what does it mean ?

thx

[/FONT]

---

### Post by #&amp;thj^% on 2018-05-06
By chance are you using Nvidia?

---

### Post by alain.roger on 2018-05-06
I'm aware about NVidia issues and i already saved in the past such problem, but unfortunately on my desktop i use an AMD Radeon RX560 graphic card and therefore i have no proprietary driver installed

---

### Post by deadflowr on 2018-05-06
In terms of startx did you setup the (or a) ~/.xinitrc file yet?
I think you need to add
```
exec startkde
```
to that file.

---

### Post by alain.roger on 2018-05-06
In fact, sometime kde starts, sometimes not... so AFAIK exec startkde it's to start kde... so if it is already started i can not work

---

### Post by #&amp;thj^% on 2018-05-06
You seem to misunderstand deadflowr's point (Or maybe is I'm not understanding you)
In your home Directory there is a hidden file there named ".xinitrc"
For example mine reads:
```
nano ~/.xinitrc
#!/bin/sh

if [ -f $HOME/.Xresources ]; then
    xrdb -merge $HOME/.Xresources
fi

exec startxfce4

```
Instead of "exec startxfce4" yours should look like "exec startkde"
Any way Good Luck I'm out.

---

### Post by alain.roger on 2018-05-06
in ubuntu 18.04 with kde 5.12 there is no .xinitrc file by default

---

### Post by #&amp;thj^% on 2018-05-06
I'm surprised at that, and that it can startx to Desktop at all let alone just sometimes.
Have a look here: [https://wiki.archlinux.org/index.php/Xinit#Autostart_X_at_login](https://wiki.archlinux.org/index.php/Xinit#Autostart_X_at_login)
Gives a couple of options to try.
I can verify this works for XFCE.
My "~/.xinitrc" Reads as I posted eariler.
```
lsb_release -rd && echo $DESKTOP_SESSION
Description:	Ubuntu 18.04 LTS
Release:	18.04
xubuntu

```

---

### Post by #&amp;thj^% on 2018-05-08
Wanted to add this and give you a courtesy Bump.
Since KDE is not my DE environment I had forgotten the past problem with"sddm" 
So if you are still effected by the startx problem, consider this as a "possible" solution.
open a konsole and type:
```
sudo dpkg-reconfigure sddm
```
and select sddm. Log out/reboot and see if things are as they should be. 
Best of Luck

---

