---
title: "Xubuntu login problem in 14.04 lts - directed to login page"
date: 2015-04-10
forum: Desktop Environments
---

### Post by PraveensNothing on 2015-04-10
Not able to login to my normal user  account. but able to login to different account 

Installation configuration.

Started ubuntu 14.04 LTS server in VMplayer and then installed xubuntu-desktop.

Desktop was working fine for some time for all account, suddenly there was some problem with vmplayer after repairing the vmplayer problem, not able to login to main account it will be directed to login page again.

My password is correct because able to login praveen account from command prompt


[HR][/HR]commands

[HR][/HR]

lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty


[HR][/HR]ls -l /etc/lightdm

total 12
drwxr-xr-x 2 root root 4096 Mar 26 18:55 lightdm.conf.d
lrwxrwxrwx 1 root root   55 Mar 26 18:53 lightdm-gtk-greeter.conf -> /etc/alternatives/lightdm-gtk-greeter-config-derivative
-rw-r--r-- 1 root root 1317 Mar 13  2014 lightdm-gtk-greeter-ubuntu.conf
-rw-r--r-- 1 root root  452 Mar 11 15:32 users.conf

[HR][/HR]cat /etc/alternatives/lightdm-gtk-greeter-config-derivative
#
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# icon-theme-name = Icon theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (none, slight, medium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
# show-indicators = semi-colon ";" separated list of allowed indicator modules. Built-in indicators include "~a11y", "~language", "~session", "~power". Unity indicators can be represented by short name (e.g. "sound", "power"), service file name, or absolute path
# show-clock (true or false)
# clock-format = strftime-format string, e.g. %H:%M
# keyboard = command to launch on-screen keyboard
# position = main window position: x y
# default-user-image = Image used as default user icon, path or #icon-name
# screensaver-timeout = Timeout (in seconds) until the screen blanks when the greeter is called as lockscreen
# 
[greeter]
background=/lib/plymouth/themes/xubuntu-logo/wallpaper.png
theme-name=Greybird
icon-theme-name=elementary-xfce-dark
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-indicators=power;~session;~language;~a11y;~power;
show-clock=true
clock-format=%d %b, %H:%M
keyboard=onboard


[HR][/HR]ls -l /home/praveens/.Xauthority

file owner is correct.



[HR][/HR]/home/praveens/.xsession-errors

nConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: logrotate main process (5624) killed by TERM signal
init: update-notifier-crash (/var/crash/_usr_sbin_apache2.0.crash) main process (5644) killed by TERM signal
init: upstart-dbus-session-bridge main process (5674) terminated with status 1
init: Disconnected from notified D-Bus bus



[HR][/HR]

looking for you help 


Best Regards

Praveen S

---

