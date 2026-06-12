---
title: "make xrandr settings permanent"
date: 2012-10-11
forum: Desktop Environments
---

### Post by maartend on 2012-10-11
I rotated my screen to the right using xrandr (xrandr --rotate right). I am now trying to make this permanent, but after logging out or rebooting, my screen is rotated back to the original position. 

I tried the following, as suggested by google and other posts:
- put the command in ~/.xprofile, ~/.xsession, ~/.xinitrc and ~/.profile
- add a session-setup-script in /etc/lightdm/lightdm.conf
- add a display-setup-script in /etc/lightdm/lightdm.conf
- add the command to the list of autostart applications
- create a file /etc/X11/Xsession.d/45custom_xrandr-settings with the command
- add the command to /etc/X11/xinit/xinitrc

None of these worked, the only result I had was that the screen was rotated at login, but immediately reverted to the original position after login with the session-setup-script and autostart methods.

I am using xubuntu 12.04 on an intel atom N270 with intel graphics.

Does anyone have any suggestions on how to get this working?

---

### Post by sledit on 2012-10-23
Greets,

I'm a bit annoyed with the behavior of randr in 12.x as well. This thread [[http://ubuntuforums.org/showthread.php?t=2074929&highlight=rotate+display]](http://ubuntuforums.org/showthread.php?t=2074929&highlight=rotate+display]) suggests that randr and xinerama conflict in the newer nvidia drivers - you can enable one but not both. It might be worth a try to make sure that its disabled in the config file[s].

luck
SL

---

### Post by volodiak on 2012-10-29
Try putting delay at the top of your randr script:
```
sleep 1 && randr ...
```
I run my randr scriopt from autostart and it works fine with 1 second sleep.

---

### Post by funicorn on 2012-10-29
Yes, all you have done is NOT the correct way to do that.  Try this way:

**[SIZE="3"]Note[/SIZE]**: Command lines in ***~/.xinitrc*** are committed one by one. So make sure each line is to be detached from xinit. If it's a daemon or a loop function, make sure it runs in the background.

**[SIZE="4"]~/.xinitrc File[/SIZE]**

> 
 #!/usr/bin/env bash  
<command_line_1>
<command_line_2>

<command_line_.> 

**[SIZE="4"]LightDM configuration[/SIZE]**

Ubuntu 12.04 uses LightDM by default.  
Create a new file /usr/share/xsessions/custom.desktop with:  
>  
[Desktop Entry] 
Name=Xsession 
Exec=/etc/X11/Xsession  

You should now have a new session option during login, Xsession will load the user's ~/.xsession file

---

### Post by paquequiereseso on 2012-11-16
I did not have the xorg.conf and did not want to run Xorg-configure. I edited */etc/ gdm/PreSession*/Default and it worked without doing anything else.
> #!/bin/sh
PATH="/usr/bin:$PATH"
#Customización xrandr
cvt 1024 768
xrandr --newmode "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
xrandr --addmode VGA-0 1024x768_75.00
xrandr --output VGA-0 --mode 1024x768_75.00
#Fin customización[SIZE=2]Use it with your own values &#8203;&#8203;resulting from cvt on Terminal.[/SIZE] Change cvt 1024 768 75 on Terminal for your desired resolution & Hz. VGA-0 or other value like VGA-1, DVI-0...  depends of result xrandr on Terminal.

---

